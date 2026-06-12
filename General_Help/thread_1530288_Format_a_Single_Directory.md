---
title: "Format a Single Directory"
date: 2010-07-13
forum: General Help
---

### Post by Moyamo on 2010-07-13
I saw it once in a forum but I can't find it anymore.  How do you format a single directory?

I need it for my backup flash disk. I use it for windows and Ubuntu pc's and use rsync to sync it, but I think the Modification times are getting mixed up as my flash drive is formatted in fat32. So I would like to format a single directory into ext4.

Thanks in Advance:p
Please Help

---

### Post by gzarkadas on 2010-07-13
I don't think you can do that. What you can do is to mount arbitrary filesystems in arbitrary directories (one fs per directory) on your / tree.

Now for your flash disk, specifically:

You should use Gparted to create two partitions. **First backup everything you want to preserve; next steps will destroy all data on the flash disk.** Erase the existing partition, then create two partitions, one at a time.

-- The **first** must be formatted as fat32 in order for Windows to be able to see it (they see only the first and they recognise only fat, not ext3/4 partitions). Set its size to the total size of your flash disk minus the size you want to allocate for backups with rsync.

-- The second can be formatted to anything you like, but for use with rsync I would recommend ext4 or ext3. Set its size to the remaining available space.

_Don't forget to format the partitions. _Also it is best to assign them labels, so that you can easliy recognise them.

When you are finished you will have a flash disk that you can use with Windows as usual (only that your rsync backups will now not be visible), as well as with Ubuntu (you will be able to use both partitions in the later case).

---

### Post by Moyamo on 2010-07-13
Thanks but the reason I didn't want a partion is that I don't know how much space I need.
So I am wondering does ntfs work better on ubuntu that fat32

---

### Post by gzarkadas on 2010-07-13
I don't know whether windows can read an ntfs flashdisk (though in principle it should). 

But you can keep the fat32 and instead use the option `--modify-window=1' in rsync's command line, as the rsync manual suggests for fat filesystems (use `man rsync' and scroll down -many pages :p - to the detailed explanation of options to find out).

---

### Post by Moyamo on 2010-07-15
Thanks !

---

### Post by dino99 on 2010-07-15
fat32 is outdated and not strong enough, use ntfs or better ext3

on linux, install ntfsprogs to deal with ntfs ( from synaptic)
on windows, install fs-drivers to deal with ext3

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Moyamo on 2010-07-15
So i'll format it in ntfs then.
Thanks alot

---

