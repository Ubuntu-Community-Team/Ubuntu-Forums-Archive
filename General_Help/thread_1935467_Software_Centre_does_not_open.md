---
title: "Software Centre does not open"
date: 2012-03-04
forum: General Help
---

### Post by AnakinSkywalker on 2012-03-04
Hello

When I click to open Ubuntu Software Centre, nothing happens. And when I use "software-center" command in Terminal, I get that error:

```
yoda@yoda-W25xHPx:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 149, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 49, in <module>
    from softwarecenter.db.application import Application
  File "/usr/share/software-center/softwarecenter/db/application.py", line 25, in <module>
    from softwarecenter.backend.channel import is_channel_available
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 25, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 165, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 148, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named LinuxMint

```

So, what can I do?
Thanks.

---

### Post by raja.genupula on 2012-03-04
```
sudo apt-get install --reinstall software-center
```
and try again .

---

### Post by AnakinSkywalker on 2012-03-04
> **raja.genupula said:**
> ```
sudo apt-get install --reinstall software-center
```
and try again .

Cheers. Worked. :=)

---

### Post by raja.genupula on 2012-03-04
hi please mark the thread as solved from thread tools and please remember this for everytime after solving your issue .

Thank you .

---

### Post by AnakinSkywalker on 2012-03-04
> **raja.genupula said:**
> hi please mark the thread as solved from thread tools and please remember this for everytime after solving your issue .

Thank you .

OK. Marked as "Solved". Thanks again.

---

