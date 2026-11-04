# Temperature Prediction with Finite Differences

Group Three's Numerical Analysis coursework applies Newton's finite-difference interpolation to estimate missing readings in a hypothetical weekly temperature dataset recorded at two-day intervals.

The notebook contains the mathematical background, implementation, results, validation examples, tests, and discussion. The example readings are illustrative and are not real weather observations.

## Project files

| File | Description |
|---|---|
| [`temperature_prediction_notebook.ipynb`](./temperature_prediction_notebook.ipynb) | Executable notebook without the cover page |
| [`temperature_prediction_notebook_.pdf`](./temperature_prediction_notebook_.pdf) | PDF without the cover page, formatted in Times New Roman, 12 pt, with 1.5 line spacing |
| [`WithCoverPage/temperature_prediction_notebook.ipynb`](./WithCoverPage/temperature_prediction_notebook.ipynb) | Notebook version with the cover page |
| [`WithCoverPage/temperature_prediction_notebook.docx`](./WithCoverPage/temperature_prediction_notebook.docx) | Editable Word submission with the cover page |
| [`WithCoverPage/temperature_prediction_notebook.pdf`](./WithCoverPage/temperature_prediction_notebook.pdf) | PDF submission with the cover page |
| [`requirements.txt`](./requirements.txt) | Python dependencies for running the notebook |
| [`kyu-logo.png`](./kyu-logo.png) | University logo used on the cover page |

## Run the notebook

Python 3.10 or later is recommended. From the project directory, create and activate a virtual environment, then install the dependencies:

### Linux or macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### Windows PowerShell

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

Open `temperature_prediction_notebook.ipynb` in Jupyter or Visual Studio Code, select the environment's Python kernel, and run all cells from top to bottom. The notebook includes:

- A comparison of MATLAB and Python
- Forward and backward finite-difference interpolation
- The difference table and estimates for the missing days
- Validation examples, input checks, and unit tests
- Accuracy and sensitivity analysis, discussion, and plots
- A reproducible simulated-week experiment with known truth, seeded measurement noise, error metrics, and plots

The notebook includes its example data and implementation; no separate dataset or command-line script is required.

## Example estimates

Using the known readings below, the notebook estimates temperatures for Days 2, 4, and 6.

| Day | Temperature (°C) | Status |
|---:|---:|---|
| 1 | 24.00 | Recorded |
| 2 | 25.44 | Estimated |
| 3 | 27.00 | Recorded |
| 4 | 28.56 | Estimated |
| 5 | 30.00 | Recorded |
| 6 | 31.19 | Estimated |
| 7 | 32.00 | Recorded |

Calculations retain full precision; the table values are rounded for display.

## Method

For equally spaced observations, Newton's forward interpolation formula is

$$
f(x)=f_0+p\Delta f_0+\frac{p(p-1)}{2!}\Delta^2 f_0+
\frac{p(p-1)(p-2)}{3!}\Delta^3 f_0+\cdots,
\qquad p=\frac{x-x_0}{h},
$$

where \(h\) is the common spacing between successive x-values. The notebook implements the finite-difference and interpolation calculations directly in Python.
