---
title: "Disk Space??"
date: 2012-02-19
forum: General Help
---

### Post by tomsn2 on 2012-02-19
If I open up the utility to check space available it changes.  I have Ubuntu installed on a 500GB drive.  I have two other drives in the machine, 500GB each, but only 1 is formatted for ext4.  Also two external drives that are NTFS.  The two other internal drives are not mounted.....so I ask how the utility can say I have 1.5TB usable?  

Also Is there a better utility that will show usage on each drive like Windows?  Thanks for the help.

---

### Post by MG&amp;TL on 2012-02-19
Are you sure you haven't setup RAID or the like? (Or let the installer do it for you?)

Can you post the output of (you need to type these commands in a terminal):

```
sudo fdisk -l
```This is a command-line utility that allows you to edit partitions, etc, but with the -l flag, it only displays devices and partitions.

```
cat /etc/fstab
```Reads the configuration files for mounting disks. 

One more question-does nautilus show other filesystems ("500 GB Filesystem" in the side pane), or does it too think that there is only one 1.5 TB drive? Btw, Ubuntu typically uses what a committee thinks are the best software choices for Ubuntu, so in a word, no, but there are *alternatives.*

---

