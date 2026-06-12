---
title: "whole drive permissions"
date: 2011-11-14
forum: General Help
---

### Post by Mount on 2011-11-14
Hi All, 

I have cloned a dying 160GB drive which contained ubuntu to the start of a 1TB drive using dd to copy. All is apparently fine and I can boot from the new  drive. Problem is I don't appear to have root permissions on the partition. For example if I right click on the root of either sda1 or sda1 or sda5 in nautilus the option to create new folder or file are greyed out however I can sudo mkdir fine from the command line. Permissions tell me than I am nor root or owner. How can this be resolved? 

Thanks, 
g

fdisk -l: for info

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9374    75290592+  83  Linux
/dev/sda2            9704       19929    82140314+   f  W95 Ext'd (LBA)
/dev/sda3            9374        9703     2648064   82  Linux swap / Solaris
/dev/sda4           19930      121602   816681984   83  Linux
/dev/sda5            9704       19929    82140313+   7  HPFS/NTFS

---

