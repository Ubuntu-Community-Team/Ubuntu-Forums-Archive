---
title: "can root mount partition so it's owned by a user?"
date: 2010-02-15
forum: General Help
---

### Post by lylex on 2010-02-15
The SD card on my laptop is now formatted (Fat16), and wired into the fstab file so it mounts at boot.  But I want that filesystem to be owned by my unprivileged user account, not by root.

Is there an option for the mount command or fstab entry that will tell root to mount the partition on the user's behalf?  

I've tried including the "user" parameter in the fstab line, thinking I might mount it in my personal .bashrc when I log-in.  This does keep root from mounting it at boot time or with "sudo mount -a", but my unpriv'd account can't mount it, saying "only root can do that".

Thanks for any advice....Lyle

---

### Post by Morbius1 on 2010-02-15
You might want to post the output of the following commands so that the folks here can see what's going on:

Open **Terminal**
Type **cat /etc/fstab**
Type **sudo blkid -c /nev/null**

The usual way to take possessions of a windows formatted partition is to add a **uid=1000** option in fstab. That will make you ( 1000 ) the owner of the mount point. You need to make sure that "1000" is the correct number for you by issuing in a Terminal the command:** id**

But rather than suggesting you just add it to fstab it would be best to see what's in there already for that partition so we don't make thing worse. 

BTW, are you sure it's formatted in FAT16 and not FAT32?

---

### Post by jamesisin on 2010-02-15
Here is a post I wrote about adding additional hard drives to an Ubuntu system:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

You should be able to use these same instructions to get your drive mounted (the modifications necessary should be apparent enough).

If you have questions you can ask them here or on my blog.

---

### Post by lylex on 2010-02-15
Putting "uid=1000,gid=1000" in the fstab entry was all I needed.  Thanks for the tip.

...Lyle

---

