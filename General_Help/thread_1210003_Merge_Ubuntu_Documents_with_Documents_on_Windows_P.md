---
title: "Merge Ubuntu Documents with Documents on Windows Partition"
date: 2009-07-10
forum: General Help
---

### Post by There Was A Time on 2009-07-10
I constantly switch between my Jaunty and Windows 7 installations, and I was wondering if there's a way to merge my documents across the partitions. Obviously, I'd want them actually on the windows partition, as Ubuntu has an easier time reading it than vice-versa.

Basically, I just want to trick Ubuntu into mounting my Windows Docs into the Ubuntu Documents Directory. Is there an easy way to do this?

If it has any relevance, I have already set the Windows drive to mount to /win/ on boot, through Fstab. I don't know it mounting a sub-directory of the same drive to a different location will cause an issue... Is this the best approach?

---

### Post by Cl0ud9 on 2009-07-10
I have three suggestions that you may find useful.

1. Create a shared FAT32 or NTFS partition to store your docs on.
2. Write a short script to run rsync upon booting into ubuntu.
```

man rsync

```
3. Change the mountpoint for your windows partition via /etc/fstab.

---

### Post by There Was A Time on 2009-07-10
I appreciate the help, and Solution 3 seems like the best at the moment, but could you explain what rsync is? And would that script go in ftsab?

---

### Post by Cl0ud9 on 2009-07-10
See this page for more info on rsync
[https://help.ubuntu.com/community/rsync]("https://help.ubuntu.com/community/rsync")

It has nothing to do with fstab, but it could be used to automatically sync two separate directories on startup and shutdown.

As for fstab see this page
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by There Was A Time on 2009-07-10
Oh, I see. I will probably just alter the mount point, as I'm not keen to stuff around with rsync. I'm sure it's fine, I just want to avoid it until I have a better idea of what I'm doing.

I don't know if you noticed me asking in the OP, but will it cause any issues if I leave the partition itself mounting to /win/ and mount sda2/Users/Ethan/Documents/ to /home/ethan/documents or should I create an empty subdirectory to mount to?

Sorry if I seem lost, I'm just still new to some of this.

---

### Post by Cl0ud9 on 2009-07-10
Create an empty subdirectory to mount to. Then change the mount point in fstab _for your windows partition only_. Also you may want to look into the users option to allow read/write access for users other than root.

See [this post]("http://ubuntuforums.org/showthread.php?t=283131") for more information

Edit:

You could set the mountpoint to /home/ethan/documents, but back up any files in /home/ethan/documents first. I suggest going with a newly created subdirectory until you figure out exactly what you are doing.

---

### Post by There Was A Time on 2009-07-11
Thanks for the help. I appreciate it. Apparently, I have no problem with read/write access, but I'll keep that in mind if anything pops up.

I just ended up leaving it mounted to Win and creating a Launcher to the right directory, placing it in /home/ethan/

---

