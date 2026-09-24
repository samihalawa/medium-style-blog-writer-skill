---
name: medium-style-blog-writer
description: Write Medium-natural blog articles and short how-to tutorials with a human voice, image plan, cover plus inline visuals, alt text, and a publish-ready Markdown package. Use when the user asks for a Medium article, blog post with images, small tutorial, how-to, step-by-step guide, field notes, explainer that should not sound like AI, or a draft that needs headlines, hooks, captions, and image prompts.
metadata:
  type: workflow
  version: "1.0"
  source: samihalawa/medium-style-blog-writer-skill
---

# Medium Style Blog Writer

Write articles people finish. Default to a Medium reader who skims the hook, the H2s, and the first sentence of each section, then decides whether to stay. Prefer short tutorials when the topic is a task someone can complete.

Do not invent lived experience, screenshots of private UIs, quotes, or statistics. If a fact is missing, research it or mark the gap. If the user supplied notes, screenshots, or a voice sample, treat those as source of truth.

## Output contract

Deliver all of the following unless the user asked for only one piece.

1. Title options (5) plus the chosen working title
2. Subtitle
3. Audience, promise, and estimated read time
4. Image plan (cover + inline)
5. Full Markdown article
6. Image prompts or asset list with alt text, captions, filenames
7. Tags (5) and a 140-155 character meta/dek
8. Three short promo lines (result, contrarian, question)

Save the article as a `.md` file when the user wants a file. Keep chat output scannable.

## Defaults

- Voice — a sharp, specific person talking to one reader. Contractions. Opinions. Concrete nouns.
- Length — small tutorial 700-1400 words. Essay or explainer 1200-2000. Do not pad to hit a number.
- Paragraphs — 1-3 sentences. Mix one-sentence punches with slightly longer lines.
- H2s — statements or mini-promises, not labels like Background or Tips.
- Images — cover plus one visual every 300-400 words, or one per tutorial step when the step is visual.
- Language — match the user. Spanish, English, or bilingual only if asked.

## Workflow

### 1. Brief

Extract or infer.

- Topic
- Form — small tutorial (default when the ask is how-to, setup, recipe, workflow, or show me how), essay, explainer, list-with-spine, field notes
- Reader — who stops scrolling
- Promise — what they can do or see differently after
- Constraints — tools, time, budget, platform, language
- Proof the user already has — notes, screenshots, URLs, numbers

If the form is unclear and the topic is a task, choose small tutorial.

### 2. Research before prose

Search when the article needs current steps, versions, prices, commands, or claims.

- Prefer primary docs over listicles
- Capture version numbers and dates
- Never invent CLI flags, UI labels, or keyboard shortcuts
- For tutorials, run or reconstruct the exact sequence when a sandbox or connected tool can do it. If you cannot run it, say so in the article and keep steps conservative

Skip research only when the user handed a complete brief and asked for voice or structure only.

### 3. Angle, then headline

Do not start drafting from a topic noun.

Write 5 one-sentence angles. Each needs a point of view, a reader, and either a constraint, a mistake, a timebox, or a result. Reject generic premises.

Then write 5 headlines using mixed formats.

- Personal result with a specific number
- Contrarian statement
- Named mistake with implied fix
- Process promise with timeframe
- Direct how-to that names the outcome

Banned in titles — ultimate, comprehensive, game-changer, delving, landscape, tapestry, unlock, supercharge.

Pick one working title. Keep the others as options.

### 4. Image plan before the draft

Plan visuals first so the prose leaves room for them.

Cover

- Concept that states the promise, not a random stock desk
- Target 1400px wide for Medium body, 1200x630 if it will also be the social/OG image
- High contrast. One subject. Readable at thumbnail size
- Prefer a generated editorial illustration, a real photo the user owns, or a clean diagram. Avoid generic laptop-and-coffee unless the article is about that exact scene

Inline

- Tutorial — one annotated screenshot, diagram, or before/after per step that changes the screen or object
- Essay — a visual after the hook and after each major turn
- Never decorate. Every image must teach, prove, or reset attention

For each image record

- Placement (after which heading or paragraph)
- Purpose
- Generation prompt or source
- Alt text (describe the content, do not stuff keywords)
- Caption (one line, human)
- Filename slug

When generating, use the environment image tools. When searching, use licensed or clearly attributable sources and write the credit in the caption. Do not hotlink random CDNs if a local or generated asset can be produced.

Generation prompt pattern

```
[subject doing the exact thing the section describes], [setting],
[lighting], [composition], editorial blog illustration,
no watermark, no unreadable fake UI text, 16:9
```

For UI steps, prefer a real screenshot or a tightly cropped mock with readable labels. Do not generate fake product chrome that could be mistaken for a real app the reader must click.

### 5. Outline

Small tutorial spine

1. Hook — the pain or the finished result in 3-6 sentences
2. What you will have when you stop — one concrete outcome
3. Time, cost, and prerequisites
4. Numbered steps. One action per step. Verb-first H3
5. What good looks like after each step
6. The two or three ways people usually break it
7. Optional next 10 minutes
8. Close — what to do with the result, not a sermon

Essay / explainer spine

1. Hook with a scene, number, confession, or named mistake
2. The claim
3. 4-6 sections that move the claim forward
4. One section that names the objection
5. Close that gives the reader a next move

H2 test — if you can swap the heading into any other article on the internet, rewrite it.

### 6. Draft

Write the article in Markdown.

Rules

- Open without Have you ever, In today's world, It's no secret, In the fast-paced X
- First three sentences must contain a specific person, object, number, or failure
- Max 3 sentences per paragraph
- Vary sentence length
- End a section with a reason to read the next one
- Code and commands in fenced blocks with a language tag. Explain the one line that matters. Do not dump a file the reader does not need
- Bold sparingly — a phrase the skimmer must catch, not whole sentences
- Pull quotes only for a line the reader would actually underline
- Do not write Key Takeaways boxes unless the user asked. In a short tutorial the prerequisites and the final check already do that job

Step template for tutorials

```
### Step N — [verb] [object]

[1-3 sentences. Where to click or what to type. What should change.]

![alt](images/step-n-slug.png)
*Caption — what the reader should notice in the frame.*

If it failed — [the usual error and the fix in one or two sentences.]
```

Insert image placeholders that match the image plan. After images exist, replace placeholders with real paths or render components.

### 7. Humanize pass

Rewrite any paragraph that could sit in any article on the topic.

- Add one sided observation when you have a real basis (user notes, a run you just did, a sourced example). Never fake a childhood or a job
- Replace abstract nouns with objects, commands, prices, timestamps
- Cut throat-clearing
- Read the H2s plus first sentences only. If that skim does not teach the article, fix structure before adding words

Banned voice (do not use unless quoting someone)

delve, tapestry, testament, realm, landscape, embark, harness, leverage, utilize, foster, underscore, showcase, unlock, elevate, robust, seamless, comprehensive, pivotal, meticulous, intricate, multifaceted, game-changer, cutting-edge, moreover, furthermore, additionally, in conclusion, it's important to note, whether you're a, look no further, dive deep, at the end of the day, in today's fast-paced

Also skip emoji-stuffed headers and the isn't just X, it's Y cadence.

### 8. Package and stop

Return the output contract. If images were generated or searched, attach or render them next to the section they belong to, not dumped at the end.

Do not add a README, changelog, or meta essay about the skill.

## Medium formatting notes

- Title field plus subtitle field. The H1 in Markdown should match the title
- Featured/cover image is separate from the first inline image when useful
- Full-width for cover and step screenshots. Avoid tiny inline icons
- Caption under every image. Alt text on every image
- Tags — specific, 5 maximum, mixed broad plus niche
- Code — fenced blocks. On Medium, long files can be GitHub gists if the user is publishing there
- Keep the piece finishable. A 9-minute tutorial that is actually 4 minutes of value will be abandoned

## Quality gate

Reject the draft if any of these are true.

- Hook is a definition or a history lesson
- Tutorial steps bundle three actions
- A command, price, or UI label was guessed
- No image plan
- Any banned voice phrase survived
- Close restates the outline instead of handing the reader a next action
- Title uses ultimate / comprehensive / game-changer

Fix those before showing the user a final draft.
