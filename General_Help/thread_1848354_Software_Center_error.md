---
title: "Software Center error"
date: 2011-09-22
forum: General Help
---

### Post by xtremesupremacy3 on 2011-09-22
Hello all,

Just installed Ubuntu 11.04 on my new laptop, everything works great although I had a Zeitgeist crash error on first boot but appears to be working again (appears to be).

When I open Ubuntu Software Center it fails to open, and when I open it in the terminal I get an error as follows:
```
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

```

Anything I can do?
Thanks

---

### Post by Beacon11 on 2011-09-22
From the terminal, run:

```
sudo apt-get update
sudo apt-get upgrade
```

Do you get any informative errors? Does that fix things?

---

### Post by xtremesupremacy3 on 2011-09-22
thank you for your response,

Unfortunately that doesn't work as I already tried that. 
Thanks for the suggestion though

---

### Post by harsac on 2011-09-22
I am also facing the same issue while trying to update, installing SSH-client or server.
Why I am trying to update is that I installed 11.4 and now not able to connect from other systems using SSH

when I try ps -ef | grep -i ssh I get 
[B]xxxx    1412  1370  0 Sep21 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
[/B]
ssh localhost
ssh: connect to host localhost port 22: Connection refused

Please help

---

