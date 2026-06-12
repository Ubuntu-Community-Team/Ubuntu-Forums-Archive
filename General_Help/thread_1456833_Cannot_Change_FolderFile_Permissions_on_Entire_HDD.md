---
title: "Cannot Change Folder/File Permissions on Entire HDD"
date: 2010-04-17
forum: General Help
---

### Post by Jonah Bron on 2010-04-17
Hello, world!

I have two drives in my computer: a 160GB and an 80GB.  The 80 holds Ubuntu, the home folder, etc.  The 160 is for other files.  I need to change the read-write permissions on the 160, but I can't.  If I do it through the GUI (right-click>permissions) it just changes back instantly.  If I do it through the command line (even with sudo), it has no effect.

How should I go about this?

Thanks!:popcorn:

---

### Post by -humanaut- on 2010-04-17
How you tried mounting it first?

---

### Post by Jonah Bron on 2010-04-17
Yes, it is mounted.  As far as I know, it has to be...

---

### Post by darolu on 2010-04-17
Editing your fstab file should do the trick, it is located at "/etc/fstab".
To know what to add, run:
```
$ sudo fdisk -l
```
Identify your 160GB partition, it probably will be /dev/sdb1 (judging by your description), so use this information for your file.

After that, create a mount point:
```
$ sudo mkdir /media/<mydisk>
```
You can choose whatever you want, finally open your fstab file with:
```
$ gksudo gedit /etc/fstab
```
Add this line at the end, in this example I'm using /dev/sdb1 change it if needed:
```
# My 160GB hard drive
/dev/sdb1 	/media/<mydisk> 	***ntfs-3g*** 	defaults,user,exec,rw 	0 	0
```
In my example, it is a NTFS formatted hard drive, if yours has another filesystem you'll need to change it accordingly.

========= OPTIONAL =========================
Using UUID is recommended, to get the UUID of your hard drive run:
```
$ sudo blkid
```
And change the "/dev/sdb1" (or w/e you have) for the UUID in your fstab:
```
UUID=49B723546D64AA24 	/media/<mydisk> 	***ntfs-3g*** 	defaults,user,exec,rw 	0 	0
```
============================================

After editing and saving your file, you should be able to mount with:
```
$ sudo mount -a
```
And it should auto-mount at start up too.

---

### Post by Jonah Bron on 2010-04-17
Okay, that's fine.  But now, it's owned by root and I can't change it back to me.  It says "operation not permitted".

---

### Post by Jonah Bron on 2010-04-17
Fixed it.  I found the solution at
[http://www.linuxforums.org/forum/debian-linux-help/58375-chown-chmod-operation-not-permitted.html#post617503](http://www.linuxforums.org/forum/debian-linux-help/58375-chown-chmod-operation-not-permitted.html#post617503)

Thanks so much for your help.  It works now!

---

