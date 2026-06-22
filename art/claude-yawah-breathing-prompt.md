# Claude Build Prompt — Ya-Wah Breathing Screen

We are replacing the current plain purple breathing screen with a “Ya-Wah Breathing Garden” screen for the My Calm Place app.

## Goal
Create a calm breathing exercise screen that feels like it belongs in the same soft pastel kitten garden world as the rest of the app.

## Supplied assets
Use these files:

- `yawah-breathing-background.webp` — garden + kitten only, no breathing text baked in.
- `yawah-inhale-orb.webp` — transparent warm inhale orb.
- `yawah-exhale-orb.webp` — transparent purple exhale orb.
- `yawah-top-card.webp` — optional transparent instruction card.
- `yawah-bottom-helper-card.webp` — optional transparent helper card.
- `yawah-progress-dot-complete.webp`
- `yawah-progress-dot-active.webp`
- `yawah-progress-dot-idle.webp`
- `yawah-breathing-concept-preview.webp` — visual reference only; do not use as the functional layered screen.

## Visual behavior
The kitten should remain part of the background. Claude/code should animate the breathing objects on top.

### Inhale phase
- Show the warm yellow orb above the kitten.
- Render text in code on top of the orb:
  - Large: `ya...`
  - Small: `Breathe in`
- Animate the orb gently growing/brighting for the inhale.

### Exhale phase
- Show the purple orb lower on the screen or transition the same orb to purple.
- Render text in code:
  - Large: `wah`
  - Small: `Breathe out`
- Animate the orb gently shrinking/softening for the exhale.

## Timing
Recommended pacing:
- Inhale / `ya...`: 4 seconds
- Exhale / `wah`: 6 seconds
- Repeat for 5 breaths

## Text rendered by app code
Do not bake text into images. Render these in code so states can change:
- `ya...`
- `wah`
- `Breathe in`
- `Breathe out`
- `Breath 1 of 5` through `Breath 5 of 5`
- Optional helper: `Breathe with me`

## Layout guidance
- Top-left home button stays in code.
- Progress dots stay in code or use supplied dot assets.
- Keep the screen soft, uncluttered, and gentle.
- Avoid the old solid purple background.
- Avoid giant clinical circles with plain text only.
- No counting flowers on this screen; those belong to the counting activity.

## Recommended layering order
1. Full-screen background: `yawah-breathing-background.webp`
2. Top nav/progress UI in code
3. Breathing orb asset
4. Orb text in code
5. Bottom helper text/card in code or `yawah-bottom-helper-card.webp`
6. Progress label in code

## Suggested component state
```js
const phases = [
  { phase: 'inhale', word: 'ya...', helper: 'Breathe in', durationMs: 4000 },
  { phase: 'exhale', word: 'wah', helper: 'Breathe out', durationMs: 6000 },
];
const totalBreaths = 5;
```
