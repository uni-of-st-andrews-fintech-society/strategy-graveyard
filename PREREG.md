# Strategy Graveyard pre-registration

**Draft for team review.** Confirm the strategy registry, data coverage and proposed methods before approval. Record the approved commit hash for the paper appendix before running any backtest.

## 1. Falsifiable claim

At least one of the 20 pre-specified trading strategies improves on buy-and-hold SPY after costs on a risk-adjusted basis. For the contribution-timing comparison, test whether dollar-cost averaging (DCA) improves terminal wealth versus investing the same starting cash immediately.

## 2. Test statistic and rejection criterion

For trading strategies, use the difference in annualized excess-return Sharpe ratios versus SPY, calculated from daily net returns over common dates (252 sessions per year, same cash rate). For DCA, use the mean paired difference in terminal wealth per dollar of starting capital across equal-length cohorts. Use a one-sided test for improvement. Proposed inference uses 10,000 paired moving-block bootstrap draws with 20 trading days per block and a fixed seed of 20261117. Resample dates jointly across trading strategies. For DCA, use non-overlapping 12-month cohorts and resample paired cohort differences separately.

Apply Holm correction at family-wise alpha 0.05 across the recorded strategy, variant and placebo trials, including exploratory attempts. Retain failed or unavailable trials in the correction count and allocate them p=1. Report unadjusted and adjusted p-values, effect sizes, and deflated Sharpe ratios where Sharpe is reported. Confirm the bootstrap and multiplicity procedure before registration.

## 3. Proposed sample dates

- In-sample: 2005-01-03 through 2018-12-31, inclusive.
- Out-of-sample: 2019-01-02 through 2025-12-31, inclusive.
- Use earlier observations only for indicator warm-up. Signals use information available by the signal close and execute no earlier than the next trading session. Keep return intervals within their respective samples. Require each DCA cohort to begin and end within its sample.
- Confirm source coverage and point-in-time availability before freezing these dates.

## 4. Planned tests

- Phase 4 pilot: SPY 50/200-day SMA crossover (long SPY when the 50-session SMA exceeds the 200-session SMA, otherwise cash), versus buy-and-hold SPY and a circular-shift placebo that shifts the position series by 252 sessions within the in-sample window. Compare the after-cost Sharpe differences on common dates.
- Phase 5: Test the fixed strategy registry in-sample. Proposed sensitivity tests for trading rules are doubled costs and execution delayed by one additional session, with each rerun logged. For DCA, propose 12 equal monthly installments, with a separate sensitivity using six installments in the same 12-month horizon.
- Phase 6: Run the eligible registered rules once out-of-sample on a frozen commit. Classify each primary specification as **works** if it shows positive improvement with adjusted p ≤ 0.05 in both samples, **worked once** if it does so in exactly one, or **never worked** if neither does within the tested samples.
- Registry to complete before approval: list all 20 strategies, inputs, point-in-time universe, signals, execution and sizing rules, fixed parameter sets, test metrics and sensitivity variants. Each strategy–parameter combination is a separate trial. Confirm whether fundamentals are available on a point-in-time basis before including value or quality specifications.

## 5. Benchmark and cost assumptions

Use dividend-inclusive buy-and-hold SPY over the same dates. Proposed base cost is 5 basis points per side on traded notional, with 10 basis points per side in the doubled-cost sensitivity. Apply base costs consistently, including benchmark entry and terminal liquidation. Credit the same cash yield to uninvested balances, using a lagged three-month Treasury bill rate converted consistently to a daily accrual. For DCA, both arms start with the same cash on the same date. The lump-sum arm invests immediately and the DCA arm earns the cash rate on its pending installments. Evaluate pre-tax results.

## 6. Proposed Phase 4 kill criterion

Stop and write a null-result paper if the in-sample 50/200 crossover fails any of these conditions: strictly positive after-cost Sharpe improvement over SPY, raw one-sided p < 0.05 for that improvement, and strictly higher after-cost Sharpe than the placebo. This gate governs whether the full study proceeds. Apply the family-wise correction to inferential claims.
