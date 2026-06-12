---
title: "VirtualBox for all"
date: 2011-07-09
forum: General Help
---

### Post by Bynw on 2011-07-09
Hi,

I've installed VirtualBox OSE and have a couple of guest OS setup. I am running Ubuntu 11.04 and VBOSE version 4.x (the most current).

Now this installs the guest OS virtual harddrives to a folder in my home directory.


How do I get other users on the same host machine access to those virtual machines within VB? Currently logging in as another user and going to Applications/Accessories/VirtualBox OSE ... the list of guest machines is empty save of course on my login.

Thanks.

---

### Post by Diametric on 2011-07-09
I use VirtualBox, but never in the way you ask...my only suggestion would be to check the Oracle/Vb site and see if they have some documentation....if memory serves there is a wiki page that might help.

---

### Post by pqwoerituytrueiwoq on 2011-07-09
i would make a separate partition for virtual drives (i always used fixed size virtual drives)
and mount in in /mnt with fstab
chmod the partition to 666 and symlink everyones ~/.VirtualBox/HardDisks to the partition in /mnt/my_partition

---

### Post by Mr. Shannon on 2011-07-09
In VirtualBox go to File->Preferences then there is a setting for Default Machine Folder.  Just change this to a shared directory and move all the virtual machines into this directory.  Make sure that all users (that you want to have access to the virtual machines) have write permissions to these files.  I have never tried this, but as long as VirtualBox does not change the permissions of these files it should work.

---

