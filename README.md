# Readability Lens

Readability Lens is a free, browser-based writing analysis tool that helps authors identify the sentences in a chapter, article, or passage that are likely to be hardest to read.

## Features

- Flesch Reading Ease score
- Estimated grade level
- Word and sentence counts
- Top 5 sentences needing the most attention
- Explanation of why each sentence was selected
- Chapter difficulty map
- Suggestions for improving difficult sentences
- 100% local browser analysis
- No backend or API key required

## Difficulty Model

Each eligible sentence receives a 0–100 difficulty score using five weighted signals:

- Word complexity — 25%
- Sentence complexity — 25%
- Readability formulas — 20%
- Structural complexity — 15%
- Relative difficulty within the chapter — 15%

The tool combines these signals and ranks the sentences within the chapter.

Names, numbers, abbreviations, headings, and very short sentences are handled separately. Syllable counts, clause counts, and passive-voice flags are heuristic estimates rather than a full grammar parse, so the results are intended as guidance.

## Evaluation

The project includes a developer evaluation workflow with:

- A development set containing deliberately different sentence types
- A held-out set for comparison against human reader ratings
- Spearman rank agreement
- Top-5 overlap/recall
- A scoring changelog showing how the model evolved

The held-out set is intended to be rated by real readers before being used for final tuning.

## AI Used

Claude was used for ideation, UI/UX design, implementation, iteration, and debugging.

One early approach relied too heavily on sentence length and standard readability formulas. That could rank a long but simple sentence above a short technical sentence. The scoring system was therefore expanded into the current five-signal model.

## Tech Stack

- HTML
- CSS
- Vanilla JavaScript
- Browser-local text analysis
- No backend
- No external AI API required at runtime

## Run Locally

Because Readability Lens is a static HTML application, it can be opened directly in a browser.

Or run a local static server:

```bash
python -m http.server
```

Then open:

http://localhost:8000

## Deployment

Readability Lens can be deployed to Vercel, Netlify, GitHub Pages, or another static hosting provider.

## Privacy

All readability analysis happens locally in the browser. The author's text is not uploaded to a server or sent to an AI API for analysis.

## Goal

Readability Lens is designed to go beyond a single readability number. Its goal is to identify specific sentences that may slow readers down and explain what makes them difficult.
