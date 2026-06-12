---
title: "Wierd file system problems"
date: 2010-05-10
forum: General Help
---

### Post by KFoder on 2010-05-10
Hi

I have recently updated from 9.10 to 10.04, and seemingly without any problems, but after a couple of days the update manager started reporting problems with the files in /var/lib/dpkg/info and /var/lib/gconf/defaults, and gedit began reporting errors in some font conf files.

An examination of the mentioned files showed many *.list files in /var/lib/dpkg/info being empty, scrambled or being links to missing files ! The same was the the problem with the %gconf* files.

I also have a directory referring to itself ! /scratchbox/users/kif/scratchbox is the same as /scratchbox.

I have booted from 10.04 live CD and run fsck -f on the disk (one 128 GB disk, one partition) without finding any problems !

If I mount the disk the directory /scratchbox/users/kif/scratchbox is empty, and the links to missing files are regular files (some scrambled though).

No files in the home area are affected.

So it looks as if the OS on the harddisk sees (makes) errors in the filesystem, but the one on the live CD does not :-o

The filesystem on the disk are ext3.

I have run a mem test without any problems.

Any ideas ?

Kim

---

### Post by dino99 on 2010-05-10
first be sure you only are using "lucid" repo into synaptic repo tab

then clean the system:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

---

### Post by KFoder on 2010-05-11
Hi dino99

Well it did help somewhat, but it didn't solve the problem with the crosslinked directories and files.

Furthermore I got a problem while trying to install the latest kernel !

All in all too many weird errors, so I decided to install from scratch, and ended up with a much faster and cleaner system.

But thanks for your help anyway.

Kim

---

