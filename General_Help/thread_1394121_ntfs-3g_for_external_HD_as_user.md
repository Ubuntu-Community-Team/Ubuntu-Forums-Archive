---
title: "ntfs-3g for external HD as user"
date: 2010-01-30
forum: General Help
---

### Post by Thucydides411 on 2010-01-30
I have an external NTFS-formatted hard drive that mounts automatically at boot time, and which I can mount as root with
$ sudo ntfs-3g /dev/sdb1 /media/WD\ Passport/

I would like to be able to mount this HD as a normal user, however. Every time I wake up my laptop from suspension and it attempts to auto-mount my external hard drive, I get the following error message:

> Error mounting: mount exited with exit code 1: helper failed with:
Error opening '/dev/sdb1': Permission denied
Failed to mount '/dev/sdb1': Permission denied
Please check '/dev/sdb1' and the ntfs-3g binary permissions,
and the mounting user ID. More explanation is provided at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

At present, my permissions are:
brw-rw---- 1 root disk 8, 17 2010-01-30 13:52 sdb1
-rwsr-xr-x 1 root root 96572 2009-03-24 00:41 ntfs-3g

My ntfs-3g version is:
ntfs-3g 2009.2.1 integrated FUSE 27 - Third Generation NTFS Driver

My fstab entry for the hard drive is:
UUID=E018580B1857DF5A /media/WD\040Passport ntfs-3g rw,users 0 0

I have had this problem for some time, although I remember ntfs-3g working perfectly about two years ago. How do I get ntfs-3g to have the same functionality as I get when I plug in the hard drive on Vista (i.e. the drive mounts in the background without me having to do anything)? I am a competent computer user, but no expert at Ubuntu. I have spent a long time searching for a fix to this problem, but haven't found anything that works. Mounting external HDs is one of those things that should "just work" in any operating system, and NTFS is not exactly an exotic format. I am surprised that this problem, which seems widespread, has been left unaddressed in several consecutive Ubuntu releases.

Any help would be appreciated,
-Greg

---

### Post by Leppie on 2010-01-30
the easiest way to accomplish auto mounting of ntfs partitions without the user having to do anything in partiticular to access those parttitions, is removing the fstab entries for the concerning partitions, installing ntfs-config:
```
sudo apt-get install ntfs-config
```
configuring ntfs-config is ridiculously simple.
add the user who needs ntfs access to the fuse group:
```
sudo adduser <username> fuse
```
that's it ;)

---

### Post by Thucydides411 on 2010-01-30
Thanks for the lightning-quick response Leppie!

Mounting as user works perfectly now. I couldn't have asked for better support.

-Greg

---

### Post by Leppie on 2010-01-30
you're welcome, glad it's working as you want it :)

---

