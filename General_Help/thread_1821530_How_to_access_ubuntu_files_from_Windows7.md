---
title: "How to access ubuntu files from Windows7 ?"
date: 2011-08-09
forum: General Help
---

### Post by lordmonkeyu on 2011-08-09
Hello everyone,
I am trying to access my ubuntu (11.04) partition (ext4) from windows 7. I have tried explore2fs but it works only with ext2 ad ext3 partitions. I have downloaded samba for sharing but as I suppose it doesn't work that way.

Any ideas ?

---

### Post by kerry_s on 2011-08-09
Did you right click-> share the folder u want to access?

---

### Post by aeiah on 2011-08-09
looks like Ext2Read can be used to read the data (not write).

if you're constantly using both ubuntu and windows on the same machine, consider setting up a data partition that both can read and write to, such as NTFS. You could map it to your 'My Documents' location in windows, and mount --bind the directories into your home folder in ubuntu

---

### Post by aeiah on 2011-08-09
> **lordmonkeyu said:**
> Hello everyone,
I have downloaded samba for sharing but as I suppose it doesn't work that way.


samba is for making files and directories accessible over a network. so this won't be useful if you're talking about a dual-boot setup and all data access is local.

---

### Post by lordmonkeyu on 2011-08-09
> **aeiah said:**
> consider setting up a data partition that both can read and write to, such as NTFS. You could map it to your 'My Documents' location in windows, and mount --bind the directories into your home folder in ubuntu

Can you tell me a little more how to do it as I am not a pr0 in ubuntu stuff :)

---

### Post by Mark Phelps on 2011-08-09
> **lordmonkeyu said:**
> Can you tell me a little more how to do it as I am not a pr0 in ubuntu stuff :)

It's not strictly "ubuntu stuff" ...

First, make sure you are able to create another partition.  To do this, open a terminal in Ubuntu and enter "sudo fdisk -lu (that's a lowercase L, not a one). That will list off your partitions.  If you only have three or less, then, you're OK.  If you have four, and they are all Primary, then you can't create anymore.

Second, go into Win7 Disk Management and shrink your win7 OS partition to make some room.  Do NOT use GParted to do this; only use the Win7 utility.  Leave the new space unallocated.

Third, boot using the Ubuntu desktop CD, choose Try Ubuntu, and open Gnome Partition Editor.  When you see the partitions, ensure that the Swap partition is not mounted.  You may have to use the menu to unmount the swap.

Now, since you're actually running from the CD, you can make further changes to the partitions.  Create a new NTFS partition in the empty space. Why do this here instead of the Win7 utility? Because the Win7 utility actually allows you to create a 5th partition -- but in the process, changes your NTFS volumes into Dynamic Disks -- which creates a whole new set of problems.

Now, boot back into Ubuntu (on the hard drive), and use Nautilus to COPY the files you want into the new partition.  Once the files are in there, open them to ensure they are OK.  Then, remove the files from their old location.

If you want, you can now boot back into the Ubuntu LiveCD and adjust the partition sizes again -- just do NOT touch the Win7 OS partition.

---

### Post by lordmonkeyu on 2011-08-09
Ok, so I already have 7 partitions (where one of it is extended holding my sda5 ( which I would like to make accessible from ubuntu) and one ext4 partition and one swap)

Is there a possibility to make this sda5 (ntfs) partition accisble from ubuntu ?

---

### Post by Wim Sturkenboom on 2011-08-09
On my system (10.04), it shows under *_Places_*. It uses the labels that I gave the partitions during the partitioning/formatting in Windows (WinXP and WinData)

It might also shown in Nautilus in the left hand pane, sometimes as something like *_120GB disk_* (or so)

---

### Post by lordmonkeyu on 2011-08-09
Ok, thanks Wim Sturkenboom I didn't see that before :/

---

