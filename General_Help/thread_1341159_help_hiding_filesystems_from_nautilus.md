---
title: "help hiding filesystems from nautilus"
date: 2009-11-29
forum: General Help
---

### Post by wamanning on 2009-11-29
this solution was posted a while back, but it's not working for my 9.10 ubuntu:

[INDENT][http://ubuntuforums.org/showthread.php?t=428196&page=4](http://ubuntuforums.org/showthread.php?t=428196&page=4)[/INDENT]

here's what i've got:

[INDENT]$  cat /usr/share/hal/fdi/preprobe/95userpolicy/10ignore-disks.fdi
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
<match key="block.device" string="/dev/sdb1">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo> [/INDENT]

but that disk, called "2_Windows" still shows up in nautilus "places" (see attached gif).

i'd appreciate any tips or help to suppress specific partitions from appearing in nautilus.

---

### Post by wamanning on 2009-11-29
HAL is not the current approach.

this is the solution:

[http://www.uluga.ubuntuforums.org/showthread.php?p=8320822](http://www.uluga.ubuntuforums.org/showthread.php?p=8320822)

---

