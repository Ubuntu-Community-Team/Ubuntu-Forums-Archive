---
title: "Apport disappears, but nothing in crash log directory"
date: 2012-05-12
forum: General Help
---

### Post by sparhawkthesecond on 2012-05-12
Hi,

I'm getting a few system crashes with Ubuntu 12.04. When they occur, apport displays an icon in the menubar, and the libnotify popup appears. However, when I try to submit the bug, the apport window often disappears. I cannot see any apport-related files in /var/crash/ .

This seems to occur all the time for certain crashes (e.g. the weather menubar widget), but apport works for other things. If I run ```
$ apport-bug linux
``` it works fine, but if I try ```
$ apport-bug
``` and select the first option for both ("Display", "I don't know") it'll crash when it tries to collect the information. FWIW this occurs if I use sudo, too. OTOH, I can run the same command and choose "External or Internal..." and "Removable...", and apport works fine.

---

### Post by sparhawkthesecond on 2012-05-12
I'm not sure if this relates to the new behaviour of apport regarding duplicates? Perhaps apport just closes without notification if you try to file a duplicate bug? Can anyone confirm this behaviour? Still, I would imagine this would not explain why it closes when I try to manually file a bug, as it wouldn't know if it were a duplicate...

---

### Post by sparhawkthesecond on 2012-05-16
Bump?

---

### Post by sparhawkthesecond on 2012-06-21
It's a [feature]("https://bugs.launchpad.net/ubuntu/+source/apport/+bug/994921"), not a bug. To get the old reporting behaviour back, edit /etc/apport/crashdb.conf , by commenting out line 23. i.e. change the line```
        'problem_types': ['Bug', 'Package'],
```to```
#        'problem_types': ['Bug', 'Package'],
```

---

