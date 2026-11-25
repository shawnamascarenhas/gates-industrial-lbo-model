# Gates Industrial LBO Model Audit Report

## Scope

This review tests the final Gates Industrial LBO workbook for formula errors, internal reconciliation, transaction mechanics, debt roll forwards, sponsor-return calculations, scenario consistency, sensitivity behavior and source documentation. It is a technical review of the portfolio model, not an audit of Gates Industrial or an investment recommendation.

Workbook reviewed: `Gates_Industrial_LBO_Final.xlsx`

## Audit conclusion

The review identified no material internal calculation errors in the tested workbook. The formula-error scan returned no matches, every control in the `Checks` tab displays `OK`, and the principal transaction and return outputs reconcile independently.

The model remains an illustrative public-information exercise. Its results depend on forecast assumptions, simplified financing terms and a static market-price reference. These limitations do not indicate a spreadsheet error, but they should remain explicit when presenting the project.

## Tests performed

| Area | Procedure | Result |
|---|---|---|
| Workbook structure | Confirmed the presence and order of all 15 worksheets | No missing model tab |
| Formula errors | Searched for `#REF!`, `#DIV/0!`, `#VALUE!`, `#NAME?`, `#N/A`, `#NUM!`, `#NULL!`, `#SPILL!` and `#CALC!` | No matches |
| Historical statements | Reviewed income-statement, balance-sheet, cash-flow and segment reconciliation controls | All tested checks display `OK` |
| Operating forecast | Reviewed segment sales, segment EBITDA, margin, capex, tax and working-capital controls | All tested checks display `OK` |
| Entry valuation | Recalculated offer price, equity purchase price and enterprise value bridge | Differences equal zero within stated tolerances |
| Sources and uses | Compared total sources with total uses and debt-tranche totals | Sources equal uses at $10,764.8m |
| Debt schedule | Reviewed debt roll forwards, amortisation, cash sweep, interest and negative-balance controls | All tested checks display `OK` |
| Sponsor returns | Recalculated exit enterprise value, equity bridge, MOIC and annualised IRR | Outputs reconcile within stated tolerances |
| Scenarios | Tested return ordering, positive EBITDA, non-negative debt and base-case linkage | Downside, base and upside ordering is consistent |
| Sensitivities | Reviewed base-case intersections and monotonic behavior across entry, exit and leverage cases | Base cases tie to the Returns tab and ranges are ordered |
| Sources | Reviewed the source register and period labels | Seven public sources documented |

## Independent reconciliations

### Entry valuation

- Offer price equals $32.4375 per share.
- Equity purchase price equals $8,316.975m.
- Enterprise value equals $10,160.175m.
- Entry EV to FY2026 EBITDA equals 12.484x.

### Sources and uses

- Total uses equal $10,764.751m.
- Funded debt equals $4,476.053m, or 5.5x entry EBITDA.
- Sponsor equity equals $5,615.197m.
- The sources-less-uses difference equals zero.

### Debt schedule

- Opening funded debt equals $4,476.053m.
- FY2030 ending funded debt equals $2,765.366m.
- Cumulative debt reduction equals $1,710.687m.
- FY2030 debt to EBITDA equals 2.921x.

### Sponsor returns

- FY2030 adjusted EBITDA equals $946.734m.
- Exit enterprise value equals $11,360.807m at 12.0x EBITDA.
- Sponsor proceeds equal $8,312.241m after debt and other claims.
- MOIC equals 1.480x.
- Five-year IRR equals 8.161%.

The workbook calculates IRR independently as `MOIC^(1 / holding period) - 1`, and the audit check ties exactly to the reported return.

## Scenario review

| Scenario | FY2030 EBITDA | FY2030 debt | Exit multiple | MOIC | IRR |
|---|---:|---:|---:|---:|---:|
| Downside | $758.7m | $3,312.2m | 10.5x | 0.78x | (4.9%) |
| Base | $946.7m | $2,765.4m | 12.0x | 1.48x | 8.2% |
| Upside | $1,071.5m | $2,423.2m | 12.5x | 1.90x | 13.7% |

The scenarios behave logically. Stronger operations raise EBITDA and free cash flow, accelerate repayment, reduce exit leverage and increase sponsor proceeds. The downside case compounds weaker earnings, slower deleveraging and a lower valuation multiple.

## Sensitivity review

The entry and exit multiple grid moves in the expected directions. Lower entry valuation improves returns, while a higher exit multiple increases proceeds. The displayed IRR range extends from approximately 1.2% to 21.0%.

Only the most favorable displayed entry and exit combination exceeds a 20% IRR. This supports the model's conclusion that the assumed entry valuation is the principal constraint rather than a presentation choice or isolated scenario assumption.

The leverage sensitivity also behaves logically, but additional debt produces only modest improvement because higher cash interest partly offsets the smaller sponsor equity cheque.

## Observations and limitations

### Annual interest convention

The debt schedule uses an annual average-balance approach. This is transparent and suitable for an academic model, but a live transaction model may use iterative calculations or more detailed intra-year repayment timing.

### Illustrative financing terms

Debt tranches, pricing, amortisation and cash-sweep terms are assumptions rather than lender commitments. A real underwriting process would replace them with financing proposals and covenant documentation.

### Public-information forecast

The forecast uses public filings and company releases without management projections, customer-level data or a quality-of-earnings report. Revenue, margin and cash-conversion assumptions therefore require wider diligence ranges than a live deal model.

### Adjusted EBITDA

Historical adjusted EBITDA uses company-reported non-GAAP information. A transaction process would test the recurrence, cash cost and lender eligibility of each adjustment before using it for valuation or debt sizing.

### Market reference date

The unaffected share price is a $25.95 snapshot dated September 4, 2026. The model should be described as valued using that reference date rather than as a current live-market valuation.

### Native application verification

The workbook package and formulas were inspected using the portfolio tooling. Before external submission, open the file once in the version of Microsoft Excel that will be used for delivery and confirm recalculation, data validation and print views. This native Excel check was not part of the automated audit.

## Submission conclusion

The workbook is internally consistent for portfolio use. Its strongest feature is the link between investment judgment and model mechanics: the company generates cash and repays debt, yet the assumed entry valuation still produces inadequate sponsor returns. Present the limitations as deliberate boundaries of a public-information academic model rather than as transaction diligence completed in practice.
