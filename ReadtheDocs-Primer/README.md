Documentation for our generic modules should be written in [**Restructured Text**](http://docutils.sourceforge.net/rst.html), compiled with [Sphinx](http://www.sphinx-doc.org/en/master/usage/quickstart.html), and built/hosted with [ReadTheDocs](https://readthedocs.org/).  This directory, when compiled, is hosted at https://[yourmodule].readthedocs.io/en/latest/

For minor changes, you can simply [Edit the file using the Github editor](https://help.github.com/articles/editing-files-in-your-repository/), which will allow you to make a Pull Request.  Once approved, your changes will be reflected in the documentation automatically! 

## Install Sphinx
For minor changes, you don't need to build the documentation!  If you want to see how your changes will look on the built site, however, you will need Sphinx installed.Sphinx packages are published on the Python Package Index. The preferred tool for installing packages from PyPI is pip. This tool is provided with all modern versions of Python.

On Linux or MacOS, you should open your terminal and run the following command.
```bash
$ pip install -U sphinx
```

After installation, type `sphinx-build --version` on the command prompt. If everything worked fine, you will see the version number for the Sphinx package you just installed.

For more information, please see the Sphinx setup guide:
http://www.sphinx-doc.org/en/master/usage/quickstart.html

## Building your changes

For more extensive edits, or when contributing new guides, you should build the documentation locally. From the `docs` root (eg `[your module]/docs/`, execute `make html`.  The built site will be in `docs/_build/html/index.html`.

## Guidelines
Please follow these guidelines when updating our docs. Let us know if you have any questions or something isn't clear.

Please place images in the same folder as the guide text file, following the convention [file_name].[n].[optional description].[extension].  For example, `configuring_page_display.3.rearrange.png` or `configuring_page_display.1.png` are both located in `docs/user_guide/` and are part of the `configuring_page_display.rst` guide.

We currently use the following syntax:
```
Title of File (using title case)
=================================

Introduction text.

.. note::

  This would show up as a boxed note to the reader. It's good for ensuring important points/hints are seen but should be used sparingly. It's also a good way to note that "This guide is under developement."


Section Title
-------------

We use double backticks to indicate ``inline-code`` including file names, function and method names, paths, etc.

Longer code-blocks should begin with the ``.. code-block:: [type]`` directive and should be indented at least one 
level. There should also be a blank line before and after it as shown below.

.. code-block:: sql

  if ($needs_documentation) {
      use $these_guidelines;
      $contribute_docs = $appreciated;
  }

Section 1.1 Title
^^^^^^^^^^^^^^^^^

The use of appropriate sections makes reading documentation and later specific details easier. Sub sections such 
as this one will be hidden unless the main section is already selected.
```

For more information on syntax, see [this RestructuredText Primer](http://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html).

Starting Docs for a new Module
------------------------------

1. Install sphinx using pip and navigate yourself into git directory. 
2. Create a `docs` folder there and go inside. Run `sphinx-quickstart` and set to your needs. Simply accept the defaults except for:
```
The project name will occur in several places in the built documentation.
> Project name: Genotypes Loader
> Author name(s): Carolyn T Caron et al., University of Saskatchewan, Pulse Bioinformatics
> Project release []: 
```
3. Create one .rst document per planned section and populate it accoding to the guidelines above. If a given section is long enough to be broken up into sub-sections then create a folder with the same name as [your section].rst and place all .rst files for that section within it.
4. For each .rst file, ensure it is added to the `toctree` for that section. The base sections should be added to the index.rst
5. Edit the index.rst: change the title  to `[My Module]: Available Documentation` and remove the `Indices and Tables` section.
6. Ensure your conf.py matches the one provided here. by comparing each section. Do not change your `project information` and pay special attention to `PHP Highlighting` and `Options for HTML output`.
7. Copy `_static` from this repo to your `docs` folder. This contains the UofS-Pulse-Binfo theme alterations.
8. Build your documentation using `make html` and check `_build/html/index.html` to ensure your documentation looks as it should.
9. Add ``_build/`` to your ``.gitignore`` file and commit your changes pushing them out to github.
10. Go to https://readthedocs.org/dashboard/ and add this module as a project.
