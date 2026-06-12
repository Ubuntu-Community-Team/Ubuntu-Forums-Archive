---
title: "Ubuntu software center wont work properly(11.04)"
date: 2011-10-04
forum: General Help
---

### Post by Niteme on 2011-10-04
I wonder if anyone can help my hairy noob ( | ) out?  

> -3000:~$ /usr/bin/software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 111, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 52, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 35, in <module>
    from softwarepane import SoftwarePane
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 54, in <module>
    from  appdetailsview_gtk import AppDetailsViewGtk as AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py", line 45, in <module>
    from softwarecenter.backend.zeitgeist_simple import zeitgeist_singleton
  File "/usr/share/software-center/softwarecenter/backend/zeitgeist_simple.py", line 25, in <module>
    from zeitgeist.client import ZeitgeistClient
  File "/usr/lib/pymodules/python2.7/zeitgeist/client.py", line 36, in <module>
    from zeitgeist.datamodel import (Event, Subject, TimeRange, StorageState,
  File "/usr/lib/pymodules/python2.7/zeitgeist/datamodel.py", line 1116, in <module>
    execfile(os.path.join(_config.datadir, "zeitgeist/ontology/zeitgeist.py"))
IOError: [Errno 2] No such file or directory: '/usr/share/zeitgeist/ontology/zeitgeist.py'

Software center is not working...             Apparently I need it so I can open deb files.  

I've been a Dos/windows guy most of my life, NOT that I want an argument just a bit of background.  Acer Aspire 3000 with 512mb memory and 64 on the video card.  Also if maybe someone can point a finger to how I might get the wireless working on it!?  I have the  built in one PLUS a linksys wireless-G notebook adapter (model WPC54G)/

Thanks!

---

### Post by oldos2er on 2011-10-04
Post moved to its own thread.

---

### Post by Niteme on 2011-10-05
Kay thanks!  Still wondering about that software center... bump

---

### Post by dino99 on 2011-10-05
sudo apt-get install synaptic
sudo synaptic

the best tool :)

---

### Post by Niteme on 2011-10-05
Am I to do something with this tool?

---

