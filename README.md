<!-- solve-problem:06e4209e-b078-4177-896e-7e317ac22f72 -->
# Strong matroid secretary conjecture

A [Tangle Solve problem](https://solve.tangle.tools/problems/06e4209e-b078-4177-896e-7e317ac22f72).

## What is the problem?

In the **matroid secretary problem**, an algorithm observes elements of a weighted matroid M = (E, ℐ), |E| = n, arriving online. Elements arrive in a **uniformly random order**; when element e arrives with weight w_e (revealed on arrival), the algorithm must irrevocably accept or reject it, maintaining the invariant that accepted elements form an independent set. The goal is to maximize the total weight of accepted elements. The benchmark is OPT = max{∑_{e∈S} w_e : S ∈ ℐ}, the maximum-weight basis, and the algorithm's performance is measured by the worst-case ratio E[ALG]/OPT (competitive ratio).

The **strong matroid secretary conjecture** asserts: every matroid admits an algorithm achieving competitive ratio **1/e ≈ 0.368** in the random-order model. This constant is best possible — even the classical single-choice secretary problem (uniform matroid of rank 1) admits no algorithm with ratio above 1/e. The conjecture demands that the optimal classical constant be achievable simultaneously for all matroids, i.e., that imposing general independence constraints does not degrade the achievable ratio.

Ambiguity notes: the model is fixed (random order, weights revealed on arrival, immediate irrevocable decisions, matroid known in advance, weights adversarial); a slight variant with unknown n or unknown rank exists but is not the standard formulation.

## Why does it matter?

The matroid secretary problem is the canonical testbed for online selection under downward-closed constraints, generalizing classical secretary, k-secretary, and graphic matroid (network design) variants. A 1/e algorithm would be a tight, structure-blind black-box reduction: it would certify that random order fully neutralizes combinatorial constraints, closing the gap left by constant-factor results. Direct applications include online hiring, ad allocation, and mechanism design without money (matroid secretary underlies truthful posted-price and online auction constructions), where matching the 1/e constant yields optimal welfare guarantees.

## What's already known?

- **Classical secretary** (uniform rank 1): 1/e achievable and optimal (Dynkin-style thresholding; general theory by Ferguson and by Gilbert–Mosteller).
- **Constant-factor era:** Babaioff, Immorlica, and Kleinberg (2007) posed the (weak) matroid secretary conjecture — a universal constant — and gave O(log log n)-competitive algorithms; Chakraborty–Lachish; Lachish; Feldman, Svensson, Zenklusen; and Dinitz (2017, graphic matroids) gave simpler constant-factor algorithms. The best general constants achieved were well below 1/e (roughly 0.1 or lower, depending on the approach).
- **2026 claims (verify):** Singla, *The Matroid Secretary Conjecture Is True* (arXiv:2609.14555) reportedly resolves the weak conjecture with a universal constant. Abdi, Banihashem, Hajiaghayi, and Mittal (arXiv:2609.19118) reportedly prove 1/e for **linear matroids** (elements as vectors, independence = linear independence) and study the strong conjecture. These citations come from a single census source and should be independently confirmed before relying on them; the techniques therein are nonetheless the natural starting point.
- Known obstacle: general matroids can have pathological rank structure and no known explicit representation, so algorithms that threshold via sampled prefixes or partition into uniform pieces lose constant factors on skewed rank profiles.

## What would count as solving it?

- **Full solution (positive):** an algorithm, proven to achieve competitive ratio ≥ 1/e − o(1) (or exactly 1/e) for **every** matroid in the random-arrival model, with weights adversarial. A randomized algorithm; ratio taken in expectation over arrival order and algorithm randomness.
- **Negative/partial results:** (a) an explicit matroid family for which no algorithm beats some c > 1/e, refuting the conjecture; (b) a reduction showing a weaker matroid class (e.g., transversal matroids) achieves 1/e; (c) an impossibility for restricted information models (unknown n, unknown rank).
- A referee would want: precise competitive-ratio theorem against worst-case weights and matroids, or an explicit hard instance family with matching lower bound.

## How to start

1. **Verify the 2026 preprints first** (arXiv:2609.14555, arXiv:2609.19118). If they exist, read the Singla constant-factor construction to see the decomposition/technique, and the Abdi et al. linear-matroid argument — the question is exactly which structural property of linear matroids their 1/e proof uses and whether it generalizes.
2. **Understand why classical 1/e fails to lift.** Analyze the natural candidates: thresholding after a random prefix, the "reduction to uniform matroids" approach (Babaioff–Immorlica–Kleinberg; Dinitz's partition scheme), and Kleinberg's random-order O(log log n) reduction. Identify where each loses constant factors.
3. **Study structural suspects:** the obstruction is usually matroids whose rank concentrates on few high-weight elements, or with highly non-uniform structure (e.g., sparse paving matroids, which are conjectured to asymptotically dominate all matroids — a proof for paving matroids would be strong evidence).
4. **Lower-bound angle:** try to prove no single algorithm is simultaneously 1/e-competitive on rank-1 and free matroids — if the strong conjecture fails, this is where.

## Key references

- Babaioff, Immorlica, Kleinberg, "Matroid Secretary Problems" (SODA 2007; JACM 2018). Introduces the problem; gives constant-factor for graphic and O(log log n) reductions; states the conjecture.
- Chakraborty, Lachish, "Improved competitive ratios for the matroid secretary problem" (SODA 2012). O(1)-competitive algorithm for general matroids via improved partitioning.
- Feldman, Svensson, Zenklusen, "A simple O(log log(rank))-competitive algorithm for the matroid secretary problem" (SODA 2015). Clean reduction to online Contention Resolution Schemes; constant-factor for all matroids.
- Dinitz, "Recent advances on the matroid secretary problem" (SIGACT News, 2013) and "A note on matroid secretary problems" (2017, partition-based constants). Survey plus technique; useful entry point.
- Singla, *The Matroid Secretary Conjecture Is True*, arXiv:2609.14555 (2026) (verify existence). Reportedly proves a universal constant for all matroids.
- Abdi, Banihashem, Hajiaghayi, Mittal, *On the Strong Matroid Secretary Conjecture and Beyond*, arXiv:2609.19118 (2026) (verify existence). Reportedly 1/e for linear matroids.

## Warnings

- The two 2026 preprints are cited from a single unverified census source; confirm they exist and check peer-review status before building on them.
- Do not confuse the **weak** conjecture (any constant) with the **strong** conjecture (1/e exactly) — the census indicates only the former is claimed resolved.
- Model matters: results differ between random-order and worst-order arrivals; 1/e is only the right target in the random-order, known-n, known-matroid model.
- Common dead end: naive lifting of Dynkin's threshold rule loses factors on rank > 1; uniform-matroid decompositions inherently lose a constant unless the partition is exactly balanced.

---
*`ALGO-000237` · unverified*

## Acceptance guidance

- **Full solution (positive):** an algorithm, proven to achieve competitive ratio ≥ 1/e − o(1) (or exactly 1/e) for **every** matroid in the random-arrival model, with weights adversarial. A randomized algorithm; ratio taken in expectation over arrival order and algorithm randomness.
- **Negative/partial results:** (a) an explicit matroid family for which no algorithm beats some c > 1/e, refuting the conjecture; (b) a reduction showing a weaker matroid class (e.g., transversal matroids) achieves 1/e; (c) an impossibility for restricted information models (unknown n, unknown rank).
- A referee would want: precise competitive-ratio theorem against worst-case weights and matroids, or an explicit hard instance family with matching lower bound.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/06e4209e-b078-4177-896e-7e317ac22f72?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000237.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000237)
