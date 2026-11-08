# 🏥 Sehat Sahara — صحت سہارا

**A bilingual (Urdu + English) AI health assistant for rural Pakistan, powered by Gemma 4.**

Built for a Kaggle competition. Sehat Sahara helps patients and community health
workers describe symptoms in Urdu or English and get simple, safe, general guidance.

> ⚠️ **Medical disclaimer:** This project is a prototype and does **not** diagnose
> or treat any condition. It gives general guidance only and always advises
> seeing a doctor for serious symptoms. It is not a substitute for professional care.

## Features

- **Check Symptoms** — patients describe symptoms and receive advice in both Urdu and English.
- **Health Worker mode** — log patient name, age, gender and symptoms along with the AI advice.
- **Patient Records** — view all records saved during the current session.
- **Structured, simple answers** — every reply follows the same format:
  - 🔍 Possible Cause (ممکنہ وجہ)
  - ⚠️ Warning Signs (خطرے کی علامات)
  - ✅ Home Care Tips (گھر میں دیکھ بھال)
  - 🏥 See Doctor If (ڈاکٹر کے پاس جائیں اگر)

## How it works

- **Model:** Gemma 4 `e4b-it` (instruction-tuned), loaded with 🤗 Transformers in `bfloat16`.
- **Prompting:** A system prompt enforces bilingual replies, simple language,
  no diagnosis, and a "please see a doctor" rule for serious symptoms.
- **Interface:** A three-tab [Gradio](https://www.gradio.app/) app.

## Run on Kaggle

1. Open the notebook in Kaggle.
2. Add the **Gemma 4** model (`google/gemma-4`, Transformers, `gemma-4-e4b-it`) via *Add Input → Models*.
3. Run all cells. Gradio prints a link to the app.

## Run locally

```bash
git clone https://github.com/tahiraWorks/sehat-sahara.git
cd sehat-sahara
pip install -r requirements.txt
```

1. In the notebook, replace the Kaggle `model_path` with the Hugging Face model ID:
   ```python
   model_path = "google/gemma-4-E4B-it"
   ```
   The weights (roughly 16 GB) download automatically the first time you run it.
2. If Hugging Face asks you to accept terms or log in for this model, do so on the
   [model page](https://huggingface.co/google/gemma-4-E4B-it), then run:
   ```bash
   huggingface-cli login
   ```
3. Run the notebook. A GPU is strongly recommended.

## Privacy notes

- Patient records are stored **in memory only** and are lost when the session ends.
- The notebook launches Gradio with `share=True`, which creates a temporary **public link**.
  Set `share=False` if you don't want the app reachable from the internet.
- Do not enter real patient data into a shared or public demo.

## Limitations

- Not clinically validated; answers may be incomplete or wrong.
- Quality of Urdu output depends on the base model.
- No persistent storage or user authentication.

## License & attribution

- Gemma is provided under Google's [Gemma Terms of Use](https://ai.google.dev/gemma/terms).

