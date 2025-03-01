.. currentmodule:: rayoptics

=========
Changelog
=========

Version 0.7.5
==============
Implemented a formatted object output protocol, the listobj_str() method, that returns a formatted, descriptive string about the object's contents. This protocol was implemented in particular for profiles and parts of the optical specification. Added a console print function listobj(obj) that will work with objects that implement a listobj_str() method; the fallback is to invoke repr(obj).

Version 0.7.4
==============
Pass 2 on the |ybar| diagram layer capability. Handle thick elements and include a top level 'sys' layer. Fix insertion of system from file. Add support for models from the `OpticalBenchHub <https://www.photonstophotos.net/GeneralTopics/Lenses/OpticalBench/OpticalBenchHub.htm>`_ portion of Bill Claff's `PhotonsToPhotos <https://www.photonstophotos.net/>`_ website. Support odd polynomial surfaces in Zemax import. Added additional control over the use of flats when drawing lens elements, see ray-optics notebook `Cell Phone lens <https://github.com/mjhoptics/ray-optics-notebooks/blob/master/Cell%20Phone%20lens.ipynb>`_ for an example. Thanks also to @wuffi for contributing 2 fixes to make the interactive ray-optics app more robust.

Version 0.7.3
==============
Miscellaneous bug fixes, see checkin comments.

Version 0.7.2
==============
Add RayFans to interactive layout. Add a multiple layer |ybar| diagram capability. Works well for thin lens systems. Systems with thick lenses (e.g. Double Gauss) don't work well. Fixes in the :mod:`~.raytr.analyses` module include getting the sign right for defocused transverse aberrations and using the image gap distance instead of parax img_dist for reference sphere definition. Miscellaneous fixes.

Version 0.7.1
==============
Switch to use of strings for :class:`~.optical.model_enums.DecenterType` and :class:`~.optical.model_enums.DimensionType`. Use of the types is now deprecated. Add listobj() methods to all :mod:`~.elem.profiles` classes that lists all of the data for each profile type. Completed the fix of `opticalglass` issue #5 by using `difflib` to find better matches; seems to almost eliminate need for .smx files. Provided an alternative replacement glass spec for .smx files that requires just the glass and catalog names. Miscellaneous other fixes.

Version 0.7.0
==============

Add :class:`~.elem.parttree.PartTree` to :class:`~.optical.opticalmodel.OpticalModel`. Many changes to get SequentialModel, ElementModel and PartTree to work in sync. Add :class:`~.elem.elements.CementedElement` element to :mod:`~.elem.elements` module. Fix paraxial image distance calculation. Fix DOE implementation for DOE on exiting side of element. Add fractional field height specification to :class:`~.raytr.opticalspec.FieldSpec`. Add a mapping interface to :class:`~.optical.opticalmodel.OpticalModel` and :class:`~.raytr.opticalspec.OpticalSpecs`; allows submodel access like opm['sm'] and opm['osp]['fov']. Add :meth:`~.seq.sequential.SequentialModel.reverse_path` method to facilitate reverse ray tracing through the model. Add semi-diameter to list of items in :meth:`~.seq.sequential.SequentialModel.add_surface` method. Add exception handling for ray trace errors in :mod:`~.raytr.analyses` module. Many miscellaneous fixes and improvements.

Version 0.6.5
==============

Fixes for ray normal calculation in Even and Radial polynomial profiles, the ray trace was incorrect for these surfaces. Add do_aperture flag to :class:`~.seq.sequential.SequentialModel` to control aperture setting by :meth:`~.seq.sequential.SequentialModel.update_model`. Miscellaneous other fixes and enhancements.

Version 0.6.4
==============

Rework :mod:`~.mpl.analysisfigure` module to better separate axis vs figure functions. Simplify default layout options, but support more complicated layouts as needed. Correctly update the model when dropping a glass onto the |ybar| diagram. Fix issue #18 and update documentation.

Version 0.6.3
==============

Fixes for aspheric ray intersection calculation, implemented by reworking the :mod:`~.elem.profiles` module. Generalize the :func:`~.elem.elements.create_mirror` fct to accept a :class:`~.elem.profiles.SurfaceProfile` instance in addition.

Version 0.6.2
==============

Fixes for .zmx import. Refactor GlassHandler to allow CODEV import to use as well.

Version 0.6.1
==============

Interpret Zemax .zmx files as having UTF-16 encoding, with a fallback to UTF-8. Push classes in :mod:`~.seq.medium` towards a common set of queries with :mod:`opticalglass` glass and catalog classes. Add :func:`~.raytr.analyses.trace_list_of_rays` specified by starting point, direction cosines and wavelength.

Version 0.6.0
==============

Add import of Zemax .zmx files. Demonstrate access to lens-designs.com collection of zemax files and use that to test import capability. Build a strong tie with :mod:`opticalglass` package, including drag and drop from a glassmap view to the layout, yybar and lens table views. Add x, y-toroids. Add a paraxial-based set vig calculation to Tools menu. Set up a protocol for aperture checking in the ray trace. Add conda installation via conda-forge.

Version 0.5.0
==============

Refactor/repackage the :mod:`~.optical` subpackage into more manageable chunks. New subpackages include :mod:`~.seq`, :mod:`~.raytr`, :mod:`~.parax`, :mod:`~.elem` and :mod:`~.oprops`. The :mod:`~.layout` and :mod:`~.diagram` modules were moved from the :mod:`~.gui` subpackage to the :mod:`~.elem` and :mod:`~.parax` subpackages, respectively. The refactoring broke reading of existing .roa files; a preprocessing step was added in the :mod:`~.roafile` module to handle mapping the old structure to the new one. Documentation and Jupyter notebooks were updated to reflect the changes. 

Version 0.4.12
==============

Misc bug fixes and improvements: draw mirror substrates consistently, old .roa files should be resaved. Consolidate InteractiveFigure color and lw control in dicts, and retrofit layout usage to match diagrams. 

Version 0.4.11
==============

Add single field monochromatic PSF calc and display. Add dashboards for jupyter notebook usage for refocusing, etc. Revisions to app manager protocols for wider usage, esp. including matplotlib Figures. Use brute force OPD calc instead of equally inclined chords until eic behavior with decentered systems is fixed.

Version 0.4.10
==============

Add add_from_file() method to OpticalModel to enable importing pieces of optical
models to a master model. Include a Jupyter notebook demonstration.

Version 0.4.9
=============

Add single panel refactoring of ray fan, spot diagram and wavefront map plots
that are designed for use in a scripting environment.

Version 0.4.8
=============

Bug fixes and doc improvements

Version 0.4.7
=============

UI improvements. For Qt app, add light and dark mode, add zoom, and pan
capabilities to InteractiveFigures, rework main menu bar. For Diagram, add
object and stop shifts, lens thickness and bending, replace node with system
option. Reorganize doc structure.

Version 0.4.6
=============

Add SpecSheet capability. V2 of |ybar| diagram with more editing capability

Version 0.4.0
=============

Add initial version of Interactive Layout (Live Layout). Work in Progress...

Version 0.3.5
=============

Update aperture import and layout rendering for y-z plane tilts and decenters

Version 0.3.0
=============

Rework packaging using PyScaffold and Versioneer. Deploy documentation to ReadTheDocs

Version 0.2.0
=============

first version of documentation support for rayoptics. continue refactoring

Version 0.1.5
=============

separate qt gui files from mpl and generic ones. add rayoptics script to start qt version

Version 0.1.0
=============

major update that reads CV files, supports Hoya, Ohara and Schott glass catalogs, computes paraxial and real rays, and has Qt UI for lens data table, 2D lens picture and glass map view.

