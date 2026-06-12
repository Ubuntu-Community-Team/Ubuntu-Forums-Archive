---
title: "Problem opening Ubunut Software Center"
date: 2012-03-06
forum: General Help
---

### Post by stimamRedraider on 2012-03-06
[SIZE=2][B][COLOR=Black]Need Help!!! Ubuntu software center wont launch. Enclosed below are the errors I am getting when I tried to open it. 
[/COLOR][/B][/SIZE]
senay-ubuntu@ubuntu:~$ sudo software-center
2012-03-06 10:32:35,248 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
Traceback (most recent call last):
  File "/usr/bin/software-center", line 151, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 243, in __init__
    self.backend = get_install_backend()
  File "/usr/share/software-center/softwarecenter/backend/installbackend.py", line 69, in get_install_backend
    from softwarecenter.backend.installbackend_impl.aptd import AptdaemonBackend
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 34, in <module>
    from aptdaemon import client
ImportError: No module named aptdaemon

[SIZE=2]**Thank you!!!**[/SIZE]

---

### Post by raja.genupula on 2012-03-06
hi ok try this 

```
sudo apt-get install --reinstall software-center
``` and try again .

---

### Post by Script Warlock on 2012-03-06
or check [this]("http://ubuntuforums.org/showthread.php?t=1752306")

---

### Post by stimamRedraider on 2012-03-06
Hi Raja,

I am still having the same problem.

---

