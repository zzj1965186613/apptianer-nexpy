# apptianer-nexpy

Apptainer (Singularity) container definition for [NeXPy](https://github.com/reflexdemon/nexpy) — a Neutron Reflectometry data analysis package.

---

## What is NeXPy?

NeXPy is a Python-based GUI application for visualizing and analyzing neutron reflectometry data. It is built on top of [NumPy](https://numpy.org/), [SciPy](https://scipy.org/), and [Matplotlib](https://matplotlib.org/).

This container packages NeXPy with **PyQt5** for the GUI interface.

---

## Build the Container

```bash
apptainer build nexpy.sif nexpy.def
```

### Prerequisites

- [Apptainer](https://apptainer.org/) (formerly Singularity) installed
- A base image `base.sif` in the current directory

---

## Run the Container

```bash
apptainer run nexpy.sif
```

---

## What's Inside

The definition installs:

- `nexpy` via pipx
- `pyqt5` and `pyqt5-tools` for GUI support
- `numpy` (rebuilt to ensure compatibility)

Key steps in `%post`:

1. Installs system dependencies and `pipx`
2. Installs NeXPy, PyQt5, and PyQt5-tools via `pipx`
3. Merges PyQt5 packages into the NeXPy virtual environment
4. Replaces numpy with a fresh install for compatibility

---

## Requirements

- Apptainer 1.0+ (or Singularity 3.x+)
- A base container image (`base.sif`) — typically Debian/Ubuntu-based with Python 3.11+

---

## License

MIT
