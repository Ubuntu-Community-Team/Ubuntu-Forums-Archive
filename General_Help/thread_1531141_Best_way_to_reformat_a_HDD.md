---
title: "Best way to reformat a HDD"
date: 2010-07-14
forum: General Help
---

### Post by djyoung4 on 2010-07-14
So I have a western digital 1 TB hard drive that used to be external but I ripped it out of its case and put it in my desktop.  Everytime I restart I have to re-mount the hard drive.  I was thinking the best way to make it automount was to reformat it but what should I use.  any help is greatly appreciated.

---

### Post by bodhi.zazen on 2010-07-14
I always just use the command line

```
mkfs.ext4 /dev/sdb1
```

change sdb1 to the appropriate partition to format.

If you prefer a graphical interface, install gparted.

---

### Post by djyoung4 on 2010-07-14
> **bodhi.zazen said:**
> I always just use the command line

```
mkfs.ext4 /dev/sdb1
```

change sdb1 to the appropriate partition to format.

If you prefer a graphical interface, install gparted.

That worked but now I can't get the HDD to automount on startup. any ideas

---

### Post by bodhi.zazen on 2010-07-14
> **djyoung4 said:**
> That worked but now I can't get the HDD to automount on startup. any ideas

Put an entry in fstab ?

---

### Post by djyoung4 on 2010-07-15
> **bodhi.zazen said:**
> Put an entry in fstab ?
by doing what.  Here is my fstab file:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=753c26f6-c832-4557-8b62-7c4d76ff8bfa none            swap    sw              0       0
```

---

### Post by bodhi.zazen on 2010-07-15
[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

Ask if you have questions after reviewing that link.

---

### Post by djyoung4 on 2010-07-16
> **bodhi.zazen said:**
> [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

Ask if you have questions after reviewing that link.

thanks for the help.  but now I have another problem that arose literally right after I did this.  My computer will not connect to the wired network its on.  It usually says it is connected to auto eth0 but that is not showing up in my connection options.  any ideas.

---

### Post by dcstar on 2010-07-16
> **djyoung4 said:**
> So I have a western digital 1 TB hard drive that used to be external but I ripped it out of its case and put it in my desktop.  Everytime I restart I have to re-mount the hard drive.  I was thinking the best way to make it automount was to reformat it but what should I use.  any help is greatly appreciated.

Install the **pysdm** package and use it.

---

### Post by dcstar on 2010-07-16
> **djyoung4 said:**
> thanks for the help.  but now I have another problem that arose literally right after I did this.  My computer will not connect to the wired network its on.  It usually says it is connected to auto eth0 but that is not showing up in my connection options.  any ideas.

Do not move threads off their original subject, start a new thread.

---

