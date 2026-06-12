---
title: "UID error"
date: 2010-06-10
forum: General Help
---

### Post by mosaic2s on 2010-06-10
I have removed the 2nd hard disk from my computer. Now it is only lucid lynx 10.04. The grub has updated itself however the error - as shown in the enclosed image - comes up every time.
I am unable to solve.

---

### Post by dcstar on 2010-06-10
> **mosaic2s said:**
> I have removed the 2nd hard disk from my computer. Now it is only lucid lynx 10.04. The grub has updated itself however the error - as shown in the enclosed image - comes up every time.
I am unable to solve.

And did you also remove the entry from /etc/fstab ?

---

### Post by mosaic2s on 2010-06-10
I had commented the ntfs remarks. not sure what else to do.

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext3    errors=remount-ro 0       1
#/dev/sda1 /media/XP     ntfs    defaults,umask=007,gid=46 0

# swap was on /dev/sdb3 during installation
#UUID=702d39fb-ba8f-4cac-8423-61038fb08322 none            swap    sw              0       0



---

### Post by bab1 on 2010-06-10
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
[COLOR="Blue"]**/dev/sdb1 **[/COLOR]/ ext3 errors=remount-ro 0 1
#/dev/sda1 /media/XP ntfs defaults,umask=007,gid=46 0

# swap was on /dev/sdb3 during installation
#[COLOR="Red"]**UUID=702d39fb-ba8f-4cac-8423-61038fb08322**[/COLOR] none swap sw 0 0
```

> **mosaic2s said:**
> I had commented the ntfs remarks. not sure what else to do.

See how the swap is ID'd by UUID (in red above)?  That is how you should ID the existing partition.  If you look at the current mounts using the command: ```
mount
```

I believe you will see that the ID has changed.  This is why you should not use /dev/s?? (see blue above).

The command to see the UUID's for all partitions is ```
sudo blkid -l

or

sudo blkid -t UUID
```

See the man pages for particulars ```
man blkid
```

---

