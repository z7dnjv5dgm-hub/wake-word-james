# wake-word-james

A custom `micro_wake_word` V2 model for the wake word **"James"**,
for use with ESPHome / Home Assistant Voice PE.

Trained locally with
[MicroWakeWordV2Trainer](https://github.com/JohnnyPrimus/MicroWakeWordV2Trainer)
on 1000 synthetic samples (100 speakers, 3 speaking rates), augmented with
Audioset background noise, MIT impulse responses and FMA music, and
contrasted against ~647,000 negative spectrograms.

## Usage

```yaml
micro_wake_word:
  id: mww
  models:
    - model: https://raw.githubusercontent.com/z7dnjv5dgm-hub/wake-word-james/main/james.json
      id: james
      probability_cutoff: 95%
```

## Measured performance

| Cutoff | Missed calls | False wakes |
|--------|--------------|-------------|
| 0.95   | 4 per 100    | ~1 per 5.3 h |
| 0.90   | ~3 per 100   | ~1 per 4 h   |
| 0.69   | 1 per 100    | ~1 per 2.7 h |
| 0.37   | none         | ~1 per 1.3 h |

"James" is a single short word, so it triggers on its own more often than
a two-part wake phrase would. Raise the cutoff if that bothers you; no
retraining needed.

Personal use. The training data carries mixed licenses - see
[data_sources.md](https://github.com/kahrendt/microWakeWord/blob/main/documentation/data_sources.md).
