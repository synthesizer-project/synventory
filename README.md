# synventory

The inventory of images used by the [Synthesizer](https://github.com/synthesizer-project/synthesizer) documentation and README.

Images live here rather than in the Synthesizer repository so that its history doesn't grow every time a plot is regenerated. The documentation links to them directly.

## Layout

| Directory | Contents |
| --- | --- |
| `branding/` | Logos and banners. |
| `diagrams/` | Explanatory figures and flowcharts. |
| `profiling/` | Performance and scaling plots produced by the profiling suite in `synthesizer/profiling` (see below). |
| `publications/` | Thumbnails for the publications pages, named by ADS bibcode. |

The profiling plots are grouped by benchmark:

| Directory | Contents |
| --- | --- |
| `profiling/pipeline/` | Pipeline timing and memory against particle count. |
| `profiling/problem_size/` | Single operations against particle count and wavelength array size. |
| `profiling/thread_scaling/` | OpenMP thread scaling of individual kernels in one process. |
| `profiling/mpi_weak/` | MPI weak scaling of the Pipeline (fixed work per rank). |
| `profiling/mpi_strong/` | MPI strong scaling of the Pipeline (fixed total work). |

## Linking to an image

Use the raw URL on the `main` branch:

```
https://raw.githubusercontent.com/synthesizer-project/synventory/main/<directory>/<file>
```

For example, in reStructuredText:

```rst
.. image:: https://raw.githubusercontent.com/synthesizer-project/synventory/main/branding/synthesizer_logo.png
```

Characters that aren't valid in a URL must be percent-encoded, e.g. the `&` in `2025A&A...704A.248Q.jpeg` becomes `%26`.

## Updating the profiling plots

The profiling plots are regenerated with `profiling/run_doc_profiling_plots.sh` and `profiling/mpi/run_mpi_scaling.sh` in the Synthesizer repository, which write them in the same groups as here. Copy them over with `profiling/move_profiling_to_synventory.sh --synventory <path to this checkout>`, which keeps the file names so the documentation links keep working.
