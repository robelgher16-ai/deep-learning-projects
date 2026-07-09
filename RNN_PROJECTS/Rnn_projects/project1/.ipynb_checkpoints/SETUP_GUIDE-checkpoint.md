# Setup Guide — Char-RNN Name Classification

This project classifies surnames by language of origin using a character-level RNN in PyTorch.

## 1. What's in this package

```
char_rnn_project/
├── char_rnn_classification.ipynb   ← the notebook, open this in Jupyter
├── requirements.txt                 ← Python packages needed
├── SETUP_GUIDE.md                   ← this file
└── data/
    └── names/
        ├── Arabic.txt
        ├── Chinese.txt
        ├── ... (18 language files total)
```

**Important:** keep `data/names/` in the same folder as the notebook — the code loads it with a
relative path (`data/names`). If you move the notebook, move the `data` folder with it.

## 2. Install Python and Jupyter (skip if already set up)

Requires Python 3.9+.

```bash
python3 -m venv venv
source venv/bin/activate        # on Windows: venv\Scripts\activate
pip install -r requirements.txt
```

## 3. Launch Jupyter

From inside the project folder (the one containing the notebook and `data/`):

```bash
jupyter notebook
```

This opens a browser tab. Click `char_rnn_classification.ipynb` to open it.

(If you prefer JupyterLab: `jupyter lab` instead.)

## 4. Run it

Use **Run → Run All Cells** (or run cells one by one with Shift+Enter, top to bottom).

- Training takes a few minutes on CPU (27 epochs over ~20,000 names). If you have a CUDA GPU,
  it will be used automatically — the first cell detects and sets this up.
- At the end you'll see a loss curve and a confusion matrix showing which languages the model
  confuses with each other.
- The last code cell lets you type in your own names and see what language the model predicts.

## 5. Common issues

- **`FileNotFoundError: data/names`** → your notebook isn't in the same folder as the `data/`
  directory, or you launched Jupyter from a different working directory. cd into the project
  folder before running `jupyter notebook`.
- **Training feels slow** → reduce `n_epoch` in the training cell (currently 27) to something
  smaller like 10 for a quicker (less accurate) run.
- **No `torch` module** → make sure you activated your virtual environment and ran
  `pip install -r requirements.txt`.

## About the project

This is the PyTorch tutorial "NLP From Scratch: Classifying Names with a Character-Level RNN"
by Sean Robertson, adapted into a runnable Jupyter notebook. It trains a simple RNN to guess a
person's language of origin from the spelling of their surname, using ~20,000 names across
18 languages.
