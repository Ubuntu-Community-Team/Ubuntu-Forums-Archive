---
title: "Nvidia detection"
date: 2009-07-26
forum: General Help
---

### Post by abhi90 on 2009-07-26
[SIZE=4][FONT=Arial][SIZE=3]I have Nvidia Geforce 4 MX 4000 graphics card... but It doesnt detect in ubuntu 9.04. I install the driver package 96.. but it cant work.. I see also hardware settiings.. In that I see the Nvidia drivers are working but it doesnt take effect....
I have turn on the _visual effect _but it doesnt take efffect on the _Normal mode_ or in the _extra mode  _
what should I do?
My PC configuration is:
Asus P4GEMX moherboard.
1 Gb of RAM.
128 Mb nvdia Geforce MX 4000 Graphics card
Pentium 4 2.7 Ghz
[/SIZE]
[/FONT][/SIZE]

---

### Post by megatenplayah on 2009-07-26
have you tried typing in a command prompt "nvidia-xconfig", and then restart x?

also, maybe show what /etc/X11/xorg.conf says

another thing you can do is put

```

Option     "ModeDebug"     "True"

```under the Device section of the xorg.conf and then show what /var/log/Xorg.0.log says

---

