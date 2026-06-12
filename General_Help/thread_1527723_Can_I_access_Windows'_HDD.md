---
title: "Can I access Windows' HDD?"
date: 2010-07-09
forum: General Help
---

### Post by uRabbit on 2010-07-09
Ubuntu is installed on my external. Can I add/edit/manage files on the internal drive that Windows is on without messing anything up (provided I don't mess with system files)?

---

### Post by mike555 on 2010-07-09
You should be able to unless their locked by permissions or encryption .

---

### Post by uRabbit on 2010-07-09
> **mike555 said:**
> You should be able to unless their locked by permissions or encryption .

Mkay. I'm originally a Mac guy, so - as you know - Mac and Windows don't play nice.

---

### Post by oldfred on 2010-07-09
I do not like using one operating system to write into another unless I have to for repairs. Reading is fine. I would suggest a separate NTFS partition for all the data you want to share. Some windows only users also suggest a separate data partition so when you have to reinstall windows you do not lose your windows data.:smile:


Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

---

### Post by WorMzy on 2010-07-09
If it's on a partition, chances are you can mount it, edit it, and delete it as you see fit.

Run blkid as root (sudo blkid) to get a list of all available partitions, their identifiers, and their type, then construct a mount statement around that info. e.g. 'mount -t ntfs /dev/sda3 /mnt'. (Obviously creating a new directory to mount each individual partition in, e.g. /mnt/partition1, /mnt/partition2, etc)

If you want to have the partition mounted every time you boot up, follow the links that oldfred has kindly provided.

---

### Post by sisco311 on 2010-07-09
> **oldfred said:**
> I do not like using one operating system to write into another unless I have to for repairs. Reading is fine. I would suggest a separate NTFS partition for all the data you want to share. Some windows only users also suggest a separate data partition so when you have to reinstall windows you do not lose your windows data.:smile:


bindfs allows you to mirror a directory to another one with permission settings. So, it is possible to mount the Windows partition with read only access for a regular users or a group (root will have write access) and remount a specific directory (e.g. (<root>\Documents and Settings\<username> or <root>\Users\<username>) with rw access. What do you think about this?

---

### Post by uRabbit on 2010-07-09
I'm working on a way to put Ubuntu onto my internal HDD without losing my data. :) See here: [http://ubuntuforums.org/showthread.php?p=9569611](http://ubuntuforums.org/showthread.php?p=9569611)

---

