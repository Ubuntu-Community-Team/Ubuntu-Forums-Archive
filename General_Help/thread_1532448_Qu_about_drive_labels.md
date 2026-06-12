---
title: "Qu about drive labels"
date: 2010-07-16
forum: General Help
---

### Post by tomayresss on 2010-07-16
I currently have 1x80GB hard drive which is partitioned (using the Ubuntu installer) as follows:

Primary Partition (ext4) 33GB (running ubuntu)
Primary Partition (NTFS) 30GB (running win xp home)
Logical Partition (FAT32) 13GB (shared space between 2 os)
Logical Partition (Swap Space) 4GB

Using the Ubuntu Disk Utility, I have relabelled the NTFS partition "WINXP".  This is showing up correctly as WINXP in both Ubuntu and Windows.  I then gave the label "UBUNTU" to the ext4 partition, however it is still showing up simply as "File System" in Ubuntu.  I then gave the label "FAT32_TRANS" to the FAT32 partition.  This is showing up fine (labelled correctly) in Windows, but not at all in Ubuntu.

So my two problems thus far are
a) I can't seem to access my shared partition from Ubuntu
b) My Ubuntu partition doesn't seem to be labelled properly

On a side note, once these issues have been sorted, I would like to hide the WINXP partition from Ubuntu so as to prevent people saving or accessing this sector when using Ubuntu.  Could someone instruct me on how this can be done?

Thanks in advance,

Tom.

---

### Post by tomayresss on 2010-07-16
Can no one help? :(

---

### Post by oldfred on 2010-07-17
I do not think the root partition will show with the label, it is the File System.

You have to mount your shared data partition to see it. Usually it does show up in the left pane of Nautilus with the file size and the label. 

I do not know exact commands or exactly how you want to hide your XP partition. I mount mine in /usr/local and create a folder for me with my ownership & permissions. But with FAT & NTFS ownership & permissions is only set at mount time.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Look into nouser and and noauto - more info here:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

This was my old entry for a FAT partition but I now have converted everything to NTFS after losing several files that were over 4GB.

# Entry for /dev/sda4 to mount directly into my home :
UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0

---

