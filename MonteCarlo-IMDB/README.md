# Monte Carlo Rendered Image Database

This is a pre-release of the dataset not intended for public distribution. A full public release will occur later in 2017.
For now citation of the dataset can be made via:

    @article{whittle2017analysis,
    	title={Analysis of Reported Error in Monte Carlo Rendered Images},
    	author={Joss Whittle, Mark Jones, Rafal Mantiuk},
    	year={2017},
    	publisher={Springer},
    	journal={The Visual Computer},
    	month={June},
    }

### Data Organization

There are currently `5` scenes in the dataset {`cbox`, `torus`, `veach_bidir`, `veach_door`, `sponza`}, each in their own folder. Each scene folder contains images rendered with `7` different rendering algorithms {`path`, `bdpt`, `pssmlt`, `mlt`, `manifold-mlt`, `erpt`, `manifold-erpt`} (where `manifold` refers to path mutations using [Manifold exploration | Jakob et. al. 2012](http://dl.acm.org/citation.cfm?id=2185554)) and at varying sample counts on a `2^{n}` sample per pixel sequence. All images are rendered at `512 x 512` resolution.

Images are orgainzed in the format: `./{scene}/{algorithm} - {samples per pixel}.png`

The `cbox` and `sponza` scenes are rendered for `2` to `65536` samples per pixel as by that point they had already converged.
The `torus`, `veach_bidir`, and `veach_door` scenes are rendered for `2` to `524288` due to the slow convergence of caustic illumination. 

All images are rendered with [Mitsuba Renderer | Jakob 2010](https://www.mitsuba-renderer.org/download.html).

Images rendered with the `pssmlt`, `mlt`, and `manifold-mlt` algorithms were only rendered to `65536` samples per pixel for all scenes due to an integer overflow bug in Mitsuba when rendering on a distributed cluster.