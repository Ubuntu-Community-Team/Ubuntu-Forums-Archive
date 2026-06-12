---
title: "Seemingly recursive mount in /media  ... can it be deleted?"
date: 2009-08-04
forum: General Help
---

### Post by jrbryner on 2009-08-04
I've started doing a night backup of my Ubuntu drive.  Going through the logs I noticed that rsync was going through /media multiple levels and copying what looks like the entire drive multiple times.  I took a look in /media through SSH and there's a few Directories:
```

lrwxrwxrwx  1 root  root     6 2007-03-06 22:37 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2007-03-06 22:37 cdrom0
lrwxrwxrwx  1 root  root     7 2007-03-06 22:37 floppy -> floppy0
drwxr-xr-x  2 root  root  4096 2007-03-06 22:37 floppy0
drwx------ 14 jason root 32768 1969-12-31 19:00 My Passport
drwxr-xr-x  2 root  root  4096 2009-06-03 00:49 sda1
drwxr-xr-x  2 root  root  4096 2009-07-01 00:30 sdb1
drwxr-xr-x  2 root  root  4096 2008-06-03 22:23 sdb5
drwxr-xr-x 18 root  root  4096 2009-06-29 22:01 sdc1

```My Passport is a USB drive that's temporary connected.  sda1, sdb1, sdb5 are all empty directories.  sdc1 is the one the seems to fold in upon itself.  So /media/sdc1 looks like so:
```

drwxrwxrwx  3 root root 4096 2009-06-29 22:01 home
drwxr-xr-x  2 root root 4096 2006-10-25 09:26 initrd
lrwxrwxrwx  1 root root   33 2009-05-12 08:57 initrd.img -> boot/initrd.img-2.6.28-11-generic
lrwxrwxrwx  1 root root   33 2009-05-11 13:01 initrd.img.old -> boot/initrd.img-2.6.27-11-generic
drwxr-xr-x 19 root root 8192 2009-05-23 10:10 lib
drwxr-xr-x  2 root root 4096 2007-03-06 22:36 lost+found
drwxr-xr-x  8 root root 4096 2009-06-29 20:33 media
drwx------  2 root root 4096 2009-06-29 20:39 mnt
drwx------  2 root root 4096 2009-06-29 20:39 opt
dr-x------  2 root root 4096 2009-06-29 20:39 proc
drwx------  2 root root 4096 2009-06-29 20:39 root
drwx------  2 root root 4096 2009-06-29 20:39 sbin
drwx------  2 root root 4096 2009-06-29 20:39 selinux
drwx------  2 root root 4096 2009-06-29 20:39 srv
drwx------  2 root root 4096 2009-06-29 20:39 sys
drwx------  2 root root 4096 2009-06-29 20:39 tmp
drwx------  2 root root 4096 2009-06-29 20:39 usr
drwx------  2 root root 4096 2009-06-29 20:39 var
lrwxrwxrwx  1 root root   30 2009-05-12 08:57 vmlinuz -> boot/vmlinuz-2.6.28-11-generic
lrwxrwxrwx  1 root root   30 2009-05-11 13:01 vmlinuz.old -> boot/vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2689 2009-05-16 23:52 xorg.conf.new

```/media/sdc1 seems to go down infinetly.  i.e. /media/sdc1/media/sdc1/media/sdc1/media/sdc1/media/sdc1/media/sdc1/media/sdc1/media/sdc1 looks like the above

What throws me off is that according to df -i I've used about 60GB of my 80GB drive.  Now, since I've noticed this, I've excluded /media from my rsync script and my backup 80GB drive has only used about 12GB.  So it seems there's a lot of data in that /media directory.  

So the big question I have is, is it safe to delete what's in that /media/sdc1 ?

---

### Post by michy99 on 2009-08-04
If I have read this correctly, sdc1 is the partition you have backed up to. So you don't want to delete everything in sdc1, you just want to delete the recursive copy of sdc1 which is on sdc1. In other words:```
rm -r /media/sdc1/media/sdc1
```Depending on permission issues, you may have to precede that command with sudo.

---

### Post by jerome1232 on 2009-08-04
Might want to add --exclude=/media to your rsync script so that doesn't happen. (My syntax might be a bit off)

---

### Post by jrbryner on 2009-08-05
> **jerome1232 said:**
> Might want to add --exclude=/media to your rsync script so that doesn't happen. (My syntax might be a bit off)
Yep, did that.  I should've mentioned that.

---

### Post by jrbryner on 2009-08-05
> **michy99 said:**
> If I have read this correctly, sdc1 is the partition you have backed up to. So you don't want to delete everything in sdc1, you just want to delete the recursive copy of sdc1 which is on sdc1. In other words:```
rm -r /media/sdc1/media/sdc1
```Depending on permission issues, you may have to precede that command with sudo.
Doing that now.  Yea, sdc1 is the drive I'm doing the backups to.  Any idea why it's recursive like that?  

The good thing is, as it's doing the delete, I can watch the % used of the drive drop.  It went from 60% down to 16%.  Wonderful.

---

