---
title: "Ubuntu software center not working (python error)"
date: 2011-10-04
forum: General Help
---

### Post by braikar on 2011-10-04
I tried running the software center and it doesn't start anymore. I tried apt-get install --reinstall, also purged it and reinstalled it to no avail.

In fact it's a python error, when I run it from the command line I get the following traceback:
```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 44, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 33, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 37, in <module>
    from appdetailsview import AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 49, in <module>
    from widgets.wkwidget import WebkitWidget
  File "/usr/share/software-center/softwarecenter/view/widgets/wkwidget.py", line 30, in <module>
    class WebkitWidget(webkit.WebView):
AttributeError: 'module' object has no attribute 'WebView'

```

Any idea how to fix that? it's probably due to an update of python, I did run an update not long ago and if I remember correctly some python packages were updated..

This is on ubuntu 10.04 amd64

---

### Post by braikar on 2011-10-16
Still nothing?
I am the only one with ubuntu 10.04 who has that problem or is there anyone else?

---

### Post by braikar on 2011-10-23
I figured it out, a bunch of corrupted files...

---

