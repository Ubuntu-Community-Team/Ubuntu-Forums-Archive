---
title: "Sudden Low Disk Space (1.9 MB in Root)"
date: 2010-03-19
forum: General Help
---

### Post by FilmAficionado on 2010-03-19
Hi,

I'd just like to start off and say I've been using Ubuntu as my full-time OS for two years now--it's been great--no more Windows at all. Every now and then I have some problems but I'm able to troubleshoot them.

Unfortunately I'm a bit stuck right now! 

Karmic Koala.

I was unable to get my computer past the loading screen, the Ubuntu logo would flicker on and off like something was wrong, and then it would *freeze* at the command prompt after asking me to login (the OS is set to start straight into Gnome).

I restarted into Grub, picked a recover profile, and hit reduce disk space... Now I am able to start my computer as normal, BUT I get an error warning:

**Low Disk Space: The volume "Filesystem root" has only 1.9 MB disk space available.**

I have a separate partition for my Home folder, and a separate partition for my root (5GB). Both are ext4. I know that most of my root was empty at least a few days ago,... 

What could have filled up all that space? How do I track down the files (I've tried Disk Usage Analyzer but I'm not seeing root?)

Any ideas where the offending files are?

Thanks!

---

### Post by mike555 on 2010-03-19
type in terminal     sudo nautilus    ,type in your password (it wont show) when nautilus opens it should be in root , empty the trash , that might help ..........

---

### Post by drs305 on 2010-03-19
Take a look at this guide on troubleshooting disk space issues:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

It provides some terminal commands and gui apps that can help find out where your free space has gone. Often it is unremoved root trash or a backup made to the wrong partition.

---

