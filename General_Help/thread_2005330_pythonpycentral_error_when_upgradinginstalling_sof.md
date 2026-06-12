---
title: "python/pycentral error when upgrading/installing software"
date: 2012-06-17
forum: General Help
---

### Post by clp32r on 2012-06-17
Hi,
I keep getting an error whenever I install updates, or new software. It's somehow related to the version of python. I have 2.7 and 3.2. It also causes a 'System error detected' followed by the request to send and error log to help fix the problem.

Here is what is spewed out from compiz:

 compizconfig-settings-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up compizconfig-settings-manager (0.9.5.92-0ubuntu3) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2372, in <module>
    main()
  File "/usr/bin/pycentral", line 2366, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1505, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7, python3.2
dpkg: error processing compizconfig-settings-manager (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 compizconfig-settings-manager

I already did:
sudo ln -s /usr/bin/python2.7 /usr/bin/python
sudo vi /usr/share/python/debian_defaults
and changed the first few lines to read:
default-version = python2.7
 
Changing all the above to python 3.2 caused the same error, but slightly different info was spewed out by compiz.

Thanks!

---

