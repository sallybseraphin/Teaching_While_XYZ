# SET Bias AI Implementation Pack

This folder contains a structured implementation package derived from `SET_Bias_Training_Material_v3.pdf`.

## Files
- `set_bias_taxonomy.json` — four bias types, 17 categories, indicator phrases, and recommended AI actions.
- `set_bias_indicator_lexicon.csv` — flat lexicon for rules engines, keyword matchers, model evaluation, or retrieval augmentation.
- `set_bias_classification_schema.json` — JSON Schema for standardized model output.
- `set_bias_classifier_prompt.md` — implementation prompt for a classifier/reviewer assistant.
- `set_bias_training_examples.jsonl` — small labeled starter set for unit tests and prompt evaluation.
- `source_material_cleaned.md` — extracted source text from the PDF, page-separated.
- `original_SET_Bias_Training_Material_v3.pdf` — original source PDF.

## Recommended pipeline
1. Normalize comment text, preserve original wording, and assign a stable comment_id.
2. Detect explicit Type 4 escalation content first: threats, harassment, unadjudicated misconduct allegations, identity abuse, deliberate misgendering, coordinated attacks, or false factual claims.
3. Detect Type 1 and Type 3 identity-coded indicators using the taxonomy and lexicon.
4. Detect Type 2 proxy indicators, but mark them as context-dependent rather than automatically biased.
5. Cluster indicators within a comment and across comments in the same course, term, instructor, and assessment event.
6. Integrate contextual evidence: grade distribution, DFW, expected grade distribution, timing of evaluation, course level, response rate, peer observation, teaching portfolio, rubrics, LMS logs, and comparator sections.
7. Apply the grade-distribution matrix and credibility-inversion/corroboration tests.
8. Generate a structured JSON finding with evidence spans, category labels, confidence, recommended review pathway, and required corroboration.
9. Never infer instructor protected identity. Use only user- or institution-supplied context, and never make a final personnel judgment automatically.

## Human-review safeguard
The classifier should flag indicators and evidence for human review. It should not make final bias findings, infer protected identities, or determine personnel consequences.

## Type 4 handling
If a comment contains threats, targeted harassment, identity abuse, unadjudicated misconduct accusations, fabricated factual claims, or coordinated attack signals, route it outside the ordinary SET workflow and exclude it from summative personnel summaries pending protective review.
