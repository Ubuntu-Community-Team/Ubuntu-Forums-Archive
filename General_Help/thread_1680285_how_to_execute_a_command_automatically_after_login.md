---
title: "how to execute a command automatically after login?"
date: 2011-02-02
forum: General Help
---

### Post by claudios on 2011-02-02
I need to execute this command after login:
gvfs-mount -d /dev/sda1
It works perfectly from terminal but it doesn't if I add it to "Startup Applications" or to rc.local.
Is there another way?

---

### Post by gwu777 on 2011-02-02
I am not sure whether these 2 threads about mounting shares at startup will help. I personally use the first solution, editing fstab, have a look:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

[http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by claudios on 2011-02-02
The second link solved my problem as much as teaching me something really useful:
nano ~/mount.sh
[INDENT]#!/bin/sh[/INDENT]
[INDENT]gvfs-mount -d /dev/sda1[/INDENT]
chmod +x ~/mount.sh
Added the script to "Startup Applications"

I was investigating the one-click mount option in gnome menu when I found out about this command, gvfs-mount.

Thanks for your help.

---

