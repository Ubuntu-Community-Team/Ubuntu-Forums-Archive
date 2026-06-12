---
title: "install programs to a different drive?"
date: 2010-03-09
forum: General Help
---

### Post by dagamer on 2010-03-09
Hi I have been using Ubuntu for quite some time now but I noticed that when Most things are installed (especially from the software center) It automatically installs to the same drive ubuntu is installed on. Is there any way to make the programs install to a different drive?

---

### Post by oldos2er on 2010-03-09
Linux installs various parts of programs (executables, configuration files, etc.) in different directories off / (root). It's certainly possible to mount other partitions as /usr, etc/, var, or whatever you wish.

Here's a graphic of Linux filesystem hierarchy: [http://geniushackers.com/blog/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg](http://geniushackers.com/blog/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg)

---

### Post by datawench on 2010-05-08
I came to this thread by searching for this exact question, and I'm afraid I'm still unenlightened. I'm aware of the file structure... the question is, can part of it be moved? Can I, for instance, put the usr directory on a second, larger drive, symlink it, and get programs to installl and run from there?

edit: I think this is what I'm looking for? [https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)

---

### Post by srs5694 on 2010-05-08
First, understand that at a certain level, Linux sees everything as a file in a single unified directory tree. There are no C: drives, D: drives, and so on as there are in Windows.

Second, read and understand the philosophy behind the [Filesystem Hierarchy Standard (FHS).](http://www.pathname.com/fhs/) This describes where everything goes in Linux.

Third, understand that partitions are mounted at particular *mount points* (empty directories). Altering where partitions are mounted enables you to adjust what partitions are used for particular purposes.

Understanding these issues will enable you to design a partition layout that balances your disk use in a reasonable way, at least in most cases. In some cases, it may be desirable to employ a Logical Volume Management (LVM) configuration to spread use evenly across awkwardly-sized disks. If a system is already installed and juggling partitions around to suit new needs is impossible, it's sometimes necessary to employ symbolic links between partitions to move files around. My own experience in about 15 years of Linux use is that this tactic is seldom necessary. It's also possible to throw the FHS rules away and install software in completely non-standard locations; however, doing so means abandoning tools like the Debian package system, so I don't recommend this.

If you read the FHS and need more advice, you'll need to provide more information. Tell us what's not fitting where, and provide the output of the "sudo fdisk -lu" and "df -h" commands. Place the output between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string to preserve formatting to improve legibility.

---

