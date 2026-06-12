---
title: "Partitioning Help"
date: 2009-09-23
forum: General Help
---

### Post by mac2irish on 2009-09-23
I just dual-booted my computer with Ubuntu as my second OS.  I forgot to partition my hard drive and just installed so it only has 2 GB of space on Ubuntu.  Is there anyway I can partition more space for ubuntu without having to uninstall it and start over again?

---

### Post by Compintuit on 2009-09-23
Yes, install the program gparted. You might be able to figure it out from there; if not, ask for more help.

---

### Post by dankdave on 2009-09-23
I should add that it's a good idea to think about how much room you want for each operating system before starting to install anything.

Take a look at

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I think people recommend to install windoze first, then install ubuntu on top of that.  I'm not sure if you're going to run into any problems with letting gparted move the ntfs files around but that might be an issue.

---

### Post by dankdave on 2009-09-23
> **Compintuit said:**
> Yes, install the program gparted. You might be able to figure it out from there; if not, ask for more help.

Oh yeah, I forgot to mention that gparted totally rocks!  Install it with

sudo apt-get install gparted

or through the synaptec package manager.

---

### Post by drs305 on 2009-09-23
> **mac2irish said:**
> I just dual-booted my computer with Ubuntu as my second OS.  I forgot to partition my hard drive and just installed so it only has 2 GB of space on Ubuntu.  Is there anyway I can partition more space for ubuntu without having to uninstall it and start over again?

mac2irish, Welcome to Ubuntu and the Ubuntu forums.

If you chose "side by side" with Windows in Step 4 and ended up with a Ubuntu partition of less than 3GB, you are the 'victim' of an installation default that has been reported as a bug and is being worked on. 

Your options are to try to expand the existing Ubuntu / partition or reinstall and change what you do in Step 4. I've written guides on both options:

If you have a 2.5 GB partition and want to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

If you have a 2.5 GB partition and want to resize the partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

