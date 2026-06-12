---
title: "Wubi/Ubuntu Help, Need to reformat Windows."
date: 2010-09-12
forum: General Help
---

### Post by r3faat1 on 2010-09-12
So I have 2 partitions, 
C:/ is Windows.
L:/ is Linux/Ubuntu via Wubi. 

The problem is I need to reformat windows, If i deleted all partitions except L:/, and re-install windows from scratch, what will happen to the Ubuntu installation via Wubi ? 
on start up will it still show me options like "Windows 7 or Ubuntu Login option" or what ? 
Im just worried because if i reinstall windows, Wubi will be gone and also I am thinking windows will mess up the boot option wubi created. Any help is appreciated guys.

oh and I LOVE UBUNTU!!!

---

### Post by Redblade20XX on 2010-09-12
_**Before you do anything always backup all your important stuff!!!!**_

Doesn't the windows cd have an option to reinstall on the same partition in which your current windows os is on???

---

### Post by oldfred on 2010-09-12
Windows does not always show things as they are. With win7 you may also have a hidden 100MB partition for boot/recovery.

A reinstall of windows will not find wubi, it know nothing about it. If you really like Ubuntu it may be time to migrate to full partitions.

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

From the designer of wubi.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

