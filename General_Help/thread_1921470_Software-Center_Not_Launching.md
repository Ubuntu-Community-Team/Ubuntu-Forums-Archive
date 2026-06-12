---
title: "Software-Center Not Launching"
date: 2012-02-06
forum: General Help
---

### Post by S3rv3r V0id on 2012-02-06
Alright, so after searching for quite some time, I was able to find many issues similar to the issues that I am experiencing. However, none of them have been exactly the same. 

Issue number one - Software Center will not launch at all. I am new to Ubuntu yes, I am running 11.10 and when I tested from my USB stick it ran just fine, but since installing it to my hard drive I have had no such luck. Here is the error message I am receiving.

2012-02-06 19:15:24,484 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
Traceback (most recent call last):
  File "/usr/bin/software-center", line 149, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 82, in <module>
    from softwarecenter.ui.gtk3.panes.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/installedpane.py", line 43, in <module>
    from softwarecenter.backend.oneconfhandler import get_oneconf_handler
  File "/usr/share/software-center/softwarecenter/backend/oneconfhandler.py", line 25, in <module>
    from softwarecenter.backend.restfulclient import get_ubuntu_sso_backend
  File "/usr/share/software-center/softwarecenter/backend/restfulclient.py", line 36, in <module>
    from lazr.restfulclient.resource import ServiceRoot
  File "/usr/lib/python2.7/dist-packages/lazr/restfulclient/__init__.py", line 19, in <module>
    
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2692, in <module>
    add_activation_listener(lambda dist: dist.activate())
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 668, in subscribe
    callback(dist)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2692, in <lambda>
    add_activation_listener(lambda dist: dist.activate())
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2196, in activate
    map(declare_namespace, self._get_metadata('namespace_packages.txt'))
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1791, in declare_namespace
    _handle_ns(packageName, path_item)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1748, in _handle_ns
    loader = importer.find_module(packageName)
  File "/usr/lib/python2.7/pkgutil.py", line 186, in find_module
    file, filename, etc = imp.find_module(subname, path)
TypeError: must be string without null bytes, not str

I will get to my next issues after I find a way to resolve this, as all of them are typically very similar to this (unable to launch Caffeine, Ubuntu One as well as a few other programs). Sorry if this has been resolved previously, but, I have been looking everywhere and have not found this particular error message elsewhere.

Appreciate any offered help....

---

