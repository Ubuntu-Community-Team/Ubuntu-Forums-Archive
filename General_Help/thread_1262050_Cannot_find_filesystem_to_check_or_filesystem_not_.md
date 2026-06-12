---
title: "Cannot find filesystem to check or filesystem not mounted with quota option."
date: 2009-09-09
forum: General Help
---

### Post by Jorsher on 2009-09-09
Hello,

I've been trying to set up disk quotas on a remote server using this tutorial (and others):
[http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html)

Here is my fstab since I'm sure it would be helpful or asked for:
>  <sys.fichiers><pt de montage><type> <options>  <dump> <pass>
/dev/sda1       /       reiserfs        defaults,rootfs,usrquota        1       2
/dev/sda2       swap    swap    defaults        0       0
proc            /proc   proc    defaults        0       0
sysfs           /sys    sysfs   defaults        0       0

If I don't add rootfs to fstab, I get this error:
> quotacheck: Cannot stat() mounted device /dev/root: No such file or directory
quotacheck: Cannot stat() mounted device /dev/root: No such file or directory
quotacheck: Cannot find filesystem to check or filesystem not mounted with quota option.

Added rootfs to fstab and restarted.  Now the only error I get is:
> quotacheck: Cannot find filesystem to check or filesystem not mounted with quota option.

Anyone have some suggestions?

Thanks!

---

### Post by Jorsher on 2009-09-09
Ok,

When set to rootfs, I'm denied permission to all files until I run:

sudo mount -o remount -t /sda1 /dev/sda1 /

So, I removed that, and still don't know what's wrong :(

---

### Post by Jorsher on 2009-09-09
Here's my mtab if this helps:

> rootfs / rootfs rw 0 0
/dev/root / reiserfs rw,usrquota 0 0
proc /proc proc rw,nosuid,nodev,noexec 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec,mode=755 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/root /dev/.static/dev reiserfs ro,usrquota 0 0
udev /dev tmpfs rw,mode=755 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec,mode=755 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0

---

### Post by ivelasco on 2009-09-09
Hello

i use quotas on a hardy server without problems.This is my fstab line concerning to /home wich is the partition with the quotas enabled:

UUID=febe7d45-591b-43da-94dc-b4077aea840b /home           jfs     relatime,usrquota,grpquota        0       2

The only diff are that I use uuid instead /dev/xxx and that you do it in the root partition.

These are the quota commands:

Command to list users on a filesystem 	repquota -u -v
Command to list groups on a filesystem 	repquota -g -v
Command to edit user's quota 		edquota -u 
Command to edit group's quota 		edquota -g 
Command to check a user's quota 	quota -v -u	
Command to check a group's quota 	quota -v -g
Command to copy a user's quota 	 	edquota -v -p
Command to copy a group's quota 	edquota -g -p
Command to turn on user quotas 		quotaon -u
Command to turn on group quotas 	quotaon -g
Command to turn off user quotas 	quotaoff -u
Command to turn off group quotas 	quotaoff -g
Command to check quotas 		quotacheck -u -g
Command to edit user grace times 	edquota -u -t
Command to edit group grace times 	edquota -g -t


Do you try it through webmin?

---

### Post by Jorsher on 2009-09-09
Thanks for the response! I really appreciate it.

This is an OVH/Kimsufi server and doesn't have the UUID.  Any of the quota commands I try return:

> quotaon: Cannot stat() mounted device /dev/root: No such file or directory

I set it up before without issue, but now keep getting this error.

Do you see anything wrong with my fstab or mtab?

---

### Post by Jorsher on 2009-09-09
UPDATE:  I installed webmin.  I checked startup, and the quota service (don't know the Linux term :P) wasn't started.  I clicked to start at bootup, and when I rebooted it was running.

HOWEVER --  I cannot enable user quotas.  I click to enable them and nothing happens.

Any ideas?

I still get the same error message posted above when trying to do quotacheck.

---

### Post by Jorsher on 2009-09-09
Installed webmin, still unable to set it up...  I'm really confused on the problem here, as I've set this up before.  I've reinstalled the same distro of Ubuntu 3 times since it was originally set up (mostly due to n00b mistakes), and it has given me the same error every time.

Here's a copy of the webmin page for filesystems:

[img]http://i284.photobucket.com/albums/ll5/J0r5h3r/Misc/webmin.png[/img]

---

### Post by Jorsher on 2009-09-09
Anyone? :(

---

### Post by ivelasco on 2009-09-10
Did you checked the log when you get the error?

take a look at [THIS]("http://ubuntuforums.org/archive/index.php/t-1014051.html") maybe helps to you.

---

### Post by Jorsher on 2009-09-10
Thanks for the link :)

Fortunately, someone skilled with Linux was kind enough to take a look at it for me.

He ended up setting a symbolic link.  I guess it's more of a work-around than fix, but it works perfectly now :)

The problem was mtab had /dev/root listed, even though it's not listed anywhere in fstab, so there were some mounting errors.  Not 100% where it stemmed from, but he set up a symlink to point /dev/root to the root directory, and everything worked.

---

