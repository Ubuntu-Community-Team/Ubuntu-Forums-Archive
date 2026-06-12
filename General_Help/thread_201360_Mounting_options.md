---
title: "Mounting options"
date: 2006-06-21
forum: General Help
---

### Post by mparker on 2006-06-21
Hi,

I'm having some issues with mounting a second disk.
I can get the disk mounted and read it fine, I just can't get anyone but root to write to the disk partition, am I missing something simple?
Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /opt        ext3    nodev,nosuid        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by ape on 2006-06-21
You're talking about the entry for /opt, correct?  What are the permissions of the /opt directory?  You must set these to allow others to write to the location.

---

### Post by mlind on 2006-06-21
Yup, that's intended behaviour.

You could create new usergroup, modify /opt directory's group permissions so that
this new group has r/w/x access to it and add add desired users to the group.

If you're just planning to use new partition as a share for everyone, mount
it below /media or /mnt instead of /opt. For instance /mnt/share.

---

### Post by aysiu on 2006-06-21
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html) may help.

---

### Post by mparker on 2006-06-21
[QUOTE=ape]You're talking about the entry for /opt, correct?  What are the permissions of the /opt directory?  You must set these to allow others to write to the location.[/QUOTE]

right i'm talking about /opt
it has permissions of 777 and is owned by myself before something's mounted on it, after it goes back to 775 and owned by root...

---

### Post by mparker on 2006-06-21
[QUOTE=mparker]right i'm talking about /opt
it has permissions of 777 and is owned by myself before something's mounted on it, after it goes back to 775 and owned by root...[/QUOTE]

Ah, 
Set teh permissions/ownership AFTER it's mounted and it takes...

Thanks

---

