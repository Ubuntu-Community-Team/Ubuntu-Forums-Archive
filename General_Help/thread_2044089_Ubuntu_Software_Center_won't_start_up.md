---
title: "Ubuntu Software Center won't start up"
date: 2012-08-18
forum: General Help
---

### Post by Macfunky on 2012-08-18
I'm not sure why but Ubuntu Software Center won't open for me. I click on the panel and the light pulses like it's about to open but it never does. Here's what i get when i put "software-center" into terminal -

conor@Junebug:~$ software-center
ERROR:root:DebFileApplication import
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
    from debfile import DebFileApplication, DebFileOpenError
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
    from softwarecenter.db.application import Application, AppDetails
  File "/usr/share/software-center/softwarecenter/db/application.py", line 27, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 194, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 169, in _get_distro
    module = __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named "Ubuntu"
Traceback (most recent call last):
  File "/usr/bin/software-center", line 140, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 50, in <module>
    from softwarecenter.db.application import Application
  File "/usr/share/software-center/softwarecenter/db/application.py", line 27, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 194, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 169, in _get_distro
    module = __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named "Ubuntu"

I am using Dreamstudio which is just a Ubuntu 12.04 with some extras. I had it installed and working ok with the same distro. This has happened since a fresh install of the same distro. Since i reinstalled it hasn't opened for me. I use synaptic most of the time so it's not too big of a deal but i'm curious as to why it won't start. Any ideas?

---

### Post by Toz on 2012-08-25
Might be related to this: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/982370]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/982370"). Does DreamStudio modify /etc/lsb-release?

---

