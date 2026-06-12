---
title: "Creating a backup partition."
date: 2006-03-03
forum: General Help
---

### Post by Rahu on 2006-03-03
I'm thinking of trying some other linux distros, but I can't seem to find a way to backup some files i have(40 gigs, and i have no dvd burner). Is there any way to create a new partition on my hdd using the free space(there is plenty), move all my files there, format the main partition and install another distro on it, then merge the two again? It would be really helpful if anyone knows of a way to do this :)

---

### Post by Xian on 2006-03-03
[QUOTE=Rahu]Is there any way to create a new partition on my hdd using the free space(there is plenty)...[/quote]

Use [Gparted](http://gparted.sourceforge.net/).
$ sudo apt-get install gparted

[QUOTE=Rahu]move all my files there...[/quote]

Use [Rsync](http://www.ss64.com/bash/rsync.html).
Should be installed by default on your system.

[QUOTE=Rahu]format the main partition and install another distro on it, then merge the two again? [/QUOTE]

Gparted + Rsync for this instance.

---

### Post by cotcot on 2006-03-04
If you move your home directory to a separate partition you get the possibility to reinstall the operating system keeping the home partition. Please read about it to know exactly how (i have never done this).
Howto move home to separate partition : [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

As you have plenty of space why not dual or triple boot other distros and mount the home of your actual distro in fstab ?

---

### Post by jobezone on 2006-03-04
I would extensively advise people to do this! In fact, I installed debian testing in my laptop the other day, and during partition, it was already possible to choose a profile, and have the rest taken care for you. For example, for Dekstop environment, it created /swap / and /home with good sizes for /home and / .

---

