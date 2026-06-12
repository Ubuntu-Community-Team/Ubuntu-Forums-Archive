---
title: "Make permission change stick"
date: 2009-08-03
forum: General Help
---

### Post by Rizado on 2009-08-03
Hi! Because of some idiotic reason whenever I change a drive permission (running sudo chmod 666 /dev/sda1) the permissions keep reverting to the default every few minutes. I can't find any info on this and I can't find any udev rules or anything concerning the harddrives. This is really bad since it will stop any application writing to the disk that is not running as root. In turn drive corruption might occur, and it is very likely to do so. In my case I want to access a partition using virtualbox.

I'm running Kubuntu Jaunty and I'm not sure if it's specific to kubuntu or a "feature" of ubuntu in general. Anyone else noticed the same thing? It seem to only affect the partitions (/dev/sda1,2,3,4...) and not the actual drive (/dev/sda). Just change permissions on some drive and check back in 10 minutes to try this.

---

### Post by mcduck on 2009-08-03
Is that perhaps a windows partition?

Windows filesystems don't support file ownership and permissions the way Linux uses them, so you can't chown or chmod stuff on FAT or NTFS partitions. For those filesystems the permissions are configured for the whole filesystem at the time it's mounted. If you want to change the permissions for the drive you need to do it by editing that drive's mount options in /etc/fstab.

---

### Post by Rizado on 2009-08-03
> **mcduck said:**
> Is that perhaps a windows partition?

Windows filesystems don't support file ownership and permissions the way Linux uses them, so you can't chown or chmod stuff on FAT or NTFS partitions. For those filesystems the permissions are configured for the whole filesystem at the time it's mounted. If you want to change the permissions for the drive you need to do it by editing that drive's mount options in /etc/fstab.No, it's the permission of the drive. /dev/sda3 and /dev/sda7 in my case. Since they exist in /dev which is on a ext3 drive permissions should stick. And they do, but after a few minutes something changes them back to root:disk and brw-rw----. 
Anyway, it only seem to affect unmounted partitions so I'm starting to suspect that it might be some mounting application that resets them.

---

### Post by mcduck on 2009-08-03
Remember, every time you read/write that partition you are reading *that* filesystem, not the one where /dev is.

It makes no difference where the /dev directory is. If the mounted filesystem doesn't support unix-style file permissions you simply can't use them like you'd use them on unix/linux file systems. There's no way how the filesystem could store those permisssions.

---

### Post by Zorael on 2009-08-04
I believe the preferred approach is to set ownership and/or file/directory masks in fstab. I don't think you ever want to be changing modes in /dev/*? Its contents are virtual and auto-generated anyway, so naturally manual changes to them will be overwritten over time.

```
# <file system>	<mount point>	<type>	<options>	<dump> <pass>
/dev/sda2	/main		ntfs	defaults,nls=utf8,**dmask=002,fmask=113,gid=1000**	0 2
```
Owned by root (default) and my group (gid 1000), octal directory mask **002** = chmod **0775** (executable to allow for entering directories), octal file mask **113** = chmod **0664** (not executable), UTF-8 encoding. Octal modes are just like normal modes, but inverted.
```
$ ls -ld /main
**drwxrwxr-x** 1 root sunspire 8192 2009-08-02 04:28 /main

$ stat /main/WINDOWS       # directory
  File: `/main/WINDOWS'
  Size: 61440           Blocks: 120        IO Block: 4096   directory
Device: 802h/2050d      Inode: 831         Links: 1
Access: (**0775/drwxrwxr-x**)  Uid: (    0/    root)   **Gid: ( 1000/sunspire)**
Access: 2009-08-01 23:18:18.000000000 +0200
Modify: 2009-08-01 22:11:12.000000000 +0200
Change: 2009-08-01 22:11:12.000000000 +0200

$ stat /main/ntldr         # file
  File: `/main/ntldr'
  Size: 250048          Blocks: 496        IO Block: 4096   regular file
Device: 802h/2050d      Inode: 1294        Links: 1
Access: (**0664/-rw-rw-r--**)  Uid: (    0/    root)   **Gid: ( 1000/sunspire)**
Access: 2008-09-18 14:25:59.000000000 +0200
Modify: 2008-04-14 14:00:00.000000000 +0200
Change: 2008-08-13 02:55:21.000000000 +0200
```

edit: check man page for mount and mount.ext3 (etc) to see what fs-specific options are available.

---

### Post by anaconda on 2009-08-04
> **Zorael said:**
> I believe the preferred approach is to set ownership and/or file/directory masks in fstab. I don't think you ever want to be changing modes in /dev/*? Its contents are virtual and auto-generated anyway, so naturally manual changes to them will be overwritten over time.


I thought exactly the same thing. You dont want to cahnge permissions from /dev/*

Try changing permissions from where the filesystem is mounted to
eg. /media/disk  (or wherever you mount that filesystem.)

---

### Post by Rizado on 2009-08-04
No you are all getting me wrong, I'm not trying to get write permissions on the partitions mounted. What I want is raw write permissions to /dev/sda3 and /dev/sda7. No amount of tinkering in fstab will give me this.

And yes, I do want to change write permissions on /dev because I want to be able to give virtualbox raw disk write permissions top the block devices without running it as root. However the permissions keep changing back!

---

### Post by Zorael on 2009-08-04
Ah, in that sense. I'm not sure that's possible without creating a script that loops and keeps reapplying the mode changes, though do prove me wrong. And I guess in the split second(s) inbetween the permissions getting autorestored and the script realizing it, you'd likely end up with data corruption, as you mentioned.

As for Kubuntu vs other environment, try doing it in a terminal session with nothing running to see if it's a daemon doing it. For all I know it could be hald.

Also, seeing as it resets to 660, you could add the user owning the virtualbox process to gid 6 (disk), but that's a big door suddenly opened.

---

### Post by geirha on 2009-08-04
Most of the device nodes (including /dev/sd*) are created each time you boot, by udev. So the proper way to change the permissions of those device nodes is to change udev rules. 

[http://en.wikipedia.org/wiki/Udev](http://en.wikipedia.org/wiki/Udev)

Btw though, they are writable to the disk group, so you could just add yourself to the disk group ...
```

sudo adduser *yourusername* disk
# Log out and back in for group membership to take effect

```

EDIT: Zorael already pointed out the latter in post #8, sorry.

---

### Post by tripwired on 2011-02-13
Old thread, but I came across the solution while trying to fix the same problem:


```

$ cat /etc/udev/rules.d/60-virtualbox.rules 
KERNEL=="sda[78]", GROUP="diskvb", OPTIONS+="last_rule"
```

This makes sda7 and sda8 (ntfs partitions) available to a VirtualBox user in group "diskvb", without having to give VirtualBox access to every device of group "disk". The "last_rule" effectively prevents any other udev rules from being applied on these devices.

Reference: [http://www.reactivated.net/writing_udev_rules.html#options](http://www.reactivated.net/writing_udev_rules.html#options)

---

