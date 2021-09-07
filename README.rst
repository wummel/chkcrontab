==========
chkcrontab
==========

Crontab linter
==============
chkcrontab is a script to check crontab files like those in
``/etc/cron.d`` and ``/etc/crontab``.  It tries to catch glaring
errors and warn on suspect lines in a crontab file.  Some valid
lines will generate warnings.  Certain silly yet valid crontab lines
will generate errors as well.

Run this by doing::

    chkcrontab crontab_file

Errors will cause a non-zero exit code.  Warnings alone will not.

To see sample output for a bad crontab, run the following::

  ./chkcrontab ./tests/test_crontab

See the ``./tests/test_crontab.disable`` crontab for how to disable
warnings and errors.

Contributions
=============
Contributions are welcome! Please add unit tests for new features
or bug fixes.  To run all the unit tests run ``./setup test``.
If you have `tox`_ installed, just run ``tox``.

You can review `coverage`_ of added tests by running
``coverage run setup.py test`` and then running
``coverage report -m``.

Note that tests are run on `Travis`_ for all supported python
versions whenever the tree on github is pushed to.

The packaged version is available via ``pip`` or ``easy_install``
as ``chkcrontab``. The project page is on `pypi`_:

The source code is available in the following locations:

* Github: https://github.com/wummel/chkcrontab

Pull requests on any of those platforms or emailed patches are fine.
Opening issues on gitlab or github is easiest, but I'll check any
of them.

Packaging
=========

For rpm distributions, ``./setup.py bdist --formats=rpm`` should make an
rpm but currently dies due to not finding the chkcrontab.1 man page.

For Debian distributions there's an additional tool that might work.

TODO
====
* Look for duplicate entries. Puppet sometimes loads up crontabs
  with dups.
* Check for backticks. (why?)
* Make sure MAILTO and PATH are set (perhaps others?).
* Add tests for command line.
* Make "acceptable filenames" a configurable thing:
  https://github.com/lyda/chkcrontab/issues/4
* Packaging: https://github.com/lyda/chkcrontab/issues/13

Credits
=======
- `Kevin Lyda`_: Who got burned one too many times by broken crontabs.

.. _`tox`: https://pypi.python.org/pypi/tox
.. _`coverage`: https://pypi.python.org/pypi/coverage
.. _`Travis`: https://travis-ci.org/lyda/chkcrontab
.. _`Kevin Lyda`: https://github.com/lyda
.. _`CheckCrontab`: http://goo.gl/7XS9q
.. _`pypi`: https://pypi.python.org/pypi/chkcrontab
