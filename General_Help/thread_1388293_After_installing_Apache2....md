---
title: "After installing Apache2..."
date: 2010-01-22
forum: General Help
---

### Post by Stigmata13 on 2010-01-22
I seem to get this error when I try to install software from the terminal, here it is:


> Setting up python2.5-minimal (2.5.4-1ubuntu6.1) ...
Linking and byte-compiling packages for runtime python2.5...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1746, in run
    pkg = DebPackage('package', pkgname, oldstyle=False)
  File "/usr/bin/pycentral", line 381, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 414, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing python2.5-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.5:
 python2.5 depends on python2.5-minimal (= 2.5.4-1ubuntu6.1); however:
  Package python2.5-minimal is not configured yet.
dpkg: error processing python2.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gda:
 python-gda depends on python2.5 (>= 2.5); however:
  Package python2.5 is not configured yet.
dpkg: error processing python-gda (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                        Errors were encountered while processing:
 python2.5-minimal
 python2.5
 python-gda
E: Sub-process /usr/bin/dpkg returned an error code (1)Does anyone know how to fix this? I'm a complete novice when it comes to linux, I'm learning but right now this is out of my scope. And help would be much appreciated... I would hate to have to do a reinstall just because of this..

---

