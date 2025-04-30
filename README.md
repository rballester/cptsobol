# CPTSobol

This code runs an example from the "[Global Sensitivity Analysis of Uncertain Parameters in Bayesian Networks](https://www.sciencedirect.com/science/article/abs/pii/S0888613X2500009X)" paper (Ballester-Ripoll and Leonelli, 2025).

In this example, we take a Bayesian network learned from the survey "Eurobarometer 93.1: standard Eurobarometer and COVID19 Pandemic" and assume that 55 of its CPT entries are uncertain: instead of fixed at the original value $\theta^0$, they are beta-distributed with mean $\theta^0$ and $\sigma^2 = 0.02$.

![image](https://github.com/user-attachments/assets/ce035a21-2e18-4f8f-b7d3-784435c9693f)

Our target quantity of interest (QoI) is `P(COUNTRYFIN = Agree)`, i.e. whether the COVID outbreak was perceived as having serious economic consequences in the respondent's country.

We use the [method of Sobol](https://en.wikipedia.org/wiki/Variance-based_sensitivity_analysis) for global sensitivity analysis to measure the influence of each uncertain CPT entry on the QoI. 

Previous methods only conducted a one-at-a-time (OAT) analysis on the uncertain CPT entries. While useful, that type of analysis is oblivious to influences that may arise due to *interactions*, i.e. what happens when more than one uncertain parameter deviates far away from its original value. In contrast, Sobol offers a global analysis, which accounts for these interactions in the form of the *Sobol total indices*. Specifically, the method returns two indices $S_i$ and $S_i^T$ for each parameter $\theta_i$, called the *variance component* and the *total index* respectively. If $S^T_i \gg S_i$ for some parameter $\theta_i$, it means that the influence of $\theta_i$ on the QoI is mainly due to interactions with other uncertain parameters.

## Citation

If you use the method, please cite:

```
@article{BRL:25,
title = {Global sensitivity analysis of uncertain parameters in {B}ayesian networks},
journal = {International Journal of Approximate Reasoning},
volume = {180},
pages = {109368},
year = {2025},
issn = {0888-613X},
doi = {https://doi.org/10.1016/j.ijar.2025.109368},
url = {https://www.sciencedirect.com/science/article/pii/S0888613X2500009X},
author = {Rafael Ballester-Ripoll and Manuele Leonelli},
keywords = {Bayesian networks, Sensitivity analysis, Sobol indices, Tensor networks, Uncertainty quantification},
}
```
