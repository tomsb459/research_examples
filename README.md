This repository contains a few examples of code used in research. Here's an outline to the files:


1. **Synthetic control code:**

-  Abadie et al. (2015) propose the synthetic control method as a way to causally evaluate the effect of a policy on some outcomes. Methods like difference-in-differences (DID) have at least two sets of assumptions and requirements. First is that multiple units are exposed to the treatment, with the treatment effect then averaged across those units relative to control units. Second, these treatment units can have different levels of the outcome prior to the policy's passage than the control units, but they are assumed to have parallel trends. 
- Synthetic control provides a way to measure a policy (or general time-based shock's) impact on some outcome that relaxes each of these assumptions. First, the method can be used to estimate the effect of a policy change on a single treatment unit as long as there are a sufficient pool of untreated/control units. Second, the method focuses on matching treatment units to a combination of control units weighted to resemble not only the level of the outcome of the treatment unit but also the trend in that outcome. This second modification is especially important if we think that the units most likely to adopt the policy are those experiencing trends in a particular direction--for instance, states that experience upticks in malpractice claims adopting tort reform; school districts experiencing rapid increases in neighborhood violence adopting a violence prevention program. 
- Abadie and co-authors provide "synth" for R-- a package to perform most of the steps required in a synthetic control analysis. However, one of the most important steps for causal inference in the method is placebo testing. In short, we 1. take each control unit, 2. pretend it was the treated unit, 3. re-estimate the synthetic control matching, 4. look at the ratio of post to pre-policy outcomes. We want this ratio to be as large as possible in the treatment unit relative to the placebo units, indicating the policy led to a large change in the trend in the outcome in the former but not the latter. The code implements this placebo testing procedure.

2. **Model robustness code**: 

- Young and Holsteen (2017) argue that one measure of model robustness is the extent to which the magnitude/sign of and inference about a treatment variable of interest changes as we iterate through all combinations of model ingredients (e.g., covariate combinations; model options). They develop a STATA module to create all model combinations and calculate robustness statistics. I develop functions to do so for use in R.

3. **Code for conjoint study:**

- Hainmueller et al. (2013; 2015) highlight the relevance of the conjoint design for social science research. Conjoint designs are an extension of traditional factorial designs used in psychology that vary a limited number of attributes across vignettes (e.g., what race and gender a vignette character is given) and estimate the effect of each on responses. Conjoints recognize the multi-dimensional nature of choice preferences and vary many attributes simultaneously. The code in the sample is designed to interface with Qualtrics for a conjoint experiment related to how features of a situation influence perceptions that the event counts as sexual assault. The top of the code contains the basic structure of a vignette coded in html with placeholders for where we'll randomize attributes (e.g., tactic perpetrator uses; perpetrator gender). The bottom javascript code randomly selects the attributes we feed into this vignette and also stores information on which attributes a particular vignette was randomized to have for use in the survey later (e.g., for use in a question that tests whether the respondent is able to correctly recall the tactic the perpetrator uses). 

4. **Code for simulations to show properties of new method for detecting variance-affecting loci**:

- In the following working paper, co-authors and I propose a new method for assessing how genetic variants contribute not to the mean of the trait (which traditional genome-wide association studies focus on) but to the trait's variance. The simulations I helped contribute to the paper assess how well the method recovers unbiased estimates of the effect of an additional minor allele (e.g., AA versus AB) on a trait's variance in the presence of confounding between an individual's genotype and the outcome. A working version of the paper is available here: https://www.biorxiv.org/content/early/2017/12/02/175596.full.pdf+html	




