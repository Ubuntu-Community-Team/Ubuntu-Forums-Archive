---
title: "umount deletes directory"
date: 2011-08-14
forum: General Help
---

### Post by doru001 on 2011-08-14
Ubuntu 10.04 lts Desktop suddenly started to delete the mountpoint directory after umount: 
mkdir dir
sudo mount -t ntfs /dev/sda1 dir
... works well ...
sudo umount dir
dir is gone 

[Another similar unanswered post.]("http://ubuntuforums.org/showthread.php?t=1380639&highlight=umount+deletes+directory")

---

### Post by sbraz on 2011-08-14
i've searched a bit, few had problems, noone solved.
is it possible that some key attributes and/or /etc/fstab has been modified?

---

### Post by doru001 on 2011-08-15
Thank you for your answer. 

It can not be /etc/fstab, I did not change it and its last modification time is well before the problem appeared. Plus, /dev/sda1 does not appear in fstab. 

In my opinion, this problem is related to Gnome's Places menu. Gnome uses other means to mount and umount /dev/sda1, not fstab but udisks ([http://ubuntuforums.org/showthread.php?p=11150382#post11150382](http://ubuntuforums.org/showthread.php?p=11150382#post11150382)), and it deletes the mount directory in /media after umount. Also, this behaviour appeared only when at least one user was logged in graphically, so only when Gnome ran. 

However, I can not be sure that the problem is related to Gnome, because the problem disappeared after reboot.

---

### Post by anaconda on 2011-08-15
Aren't mount directories under /media/ supposed to be deleted after unmount?

The permanent mountpoints are usually located under /mnt/

I thought so anyway.

---

### Post by dcstar on 2011-08-15
> **anaconda said:**
> Aren't mount directories under /media/ supposed to be deleted after unmount?

The permanent mountpoints are usually located under /mnt/

I thought so anyway.

Exactly, /media is a **system** folder for **system** use, not for users to muck around with.

---

### Post by ezander on 2012-12-02
I'm using Ubunut 12.04 and have the same problem. My mount point is deleted regardless whether it was in /media, /mnt or some other place. Though I haven't found the culprit for this strange behaviour, one easy workaround is the following: after 'mkdir mntpoint' create a dummy file in that directory, e.g. 'touch mntpoint/.dont_delete_me', and after 'umount mntpoint' the directory will still be there.

---

