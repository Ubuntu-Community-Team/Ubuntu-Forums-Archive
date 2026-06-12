---
title: "NTFS drive appears twice in &quot;Places&quot;"
date: 2010-08-26
forum: General Help
---

### Post by pmulgaonkar on 2010-08-26
I recently upgraded to 10.04, and and now seeing strange behaviour that I hope someone can  help explain/fix. I have an NTFS hard drive that shows up twice in "Places" with the same name (Video Drive). One of these icons I can click on, and it mounts, opens etc. with no errors. The second of these icons does not mount or open, but gives an error:

```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```

There is only one reference to the actual drive in /etc/fstab

```

 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4a7af96e-b83a-4bc8-81d2-9608a053f900 /               ext4    errors=remount
-ro 0       1
# /home was on /dev/sda2 during installation
UUID=10ef3017-6d30-4926-b1ce-4a1df8259b09 /home           ext4    defaults      
  0       2
# swap was on /dev/sda3 during installation
UUID=9bbe9516-f4c6-4376-8998-0fe838b5158e none            swap    sw            
  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=2604BAB004BA81FB /media/Video\040Drive ntfs-3g users 0 0

```

It is the last drive in the list with UUID=...81FB

I don't know why it appears twice in Places, and how I can get rid of the second item.

Help much appreciated.

--prasanna

---

### Post by mc4man on 2010-08-26
I believe this may be your issue, though I saw it myself with an ext3 partition.
[https://bugs.launchpad.net/gvfs/+bug/442130](https://bugs.launchpad.net/gvfs/+bug/442130)

If so, the workaround is very straightforward, instead of UUID=xxxxx... you'll use /dev/disk/by-uuid/xxxxx... 
 read here (some example edits
[http://ubuntuforums.org/showthread.php?t=1278039&page=2](http://ubuntuforums.org/showthread.php?t=1278039&page=2)

If unsure post back, in any case it's usually prudent to backup your current fstab before editing

sudo cp /etc/fstab /etc/fstab.bak

---

### Post by pmulgaonkar on 2010-08-27
Thanks. That did the trick. Had not stumbled upon the solution despite multiple different search queries.

---

