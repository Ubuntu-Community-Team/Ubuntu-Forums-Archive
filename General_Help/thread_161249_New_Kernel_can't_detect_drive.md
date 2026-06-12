---
title: "New Kernel can't detect drive?"
date: 2006-04-16
forum: General Help
---

### Post by Union Jack on 2006-04-16
Greetings everyone :) I"m not really a linux newbie at all. I've ran many distros for.. going on 4 years now but i've never seen a problem like this one. :-k 

I just installed the 2.6.16.5 kernel, left all my settings the way they were in the config and only added a few optinos to increase my performance (CFQ, Preemptable kernel, Timer Freq., etc.) But when i restart and run it, it gives me the message in the failsafe terminal "Can't mount /dev/hdb1 maybe it is already mounted or /home is in use". Now i've checked and made sure i was NOT in the /home dir at the time and when i went to umount it, it said it wasn't mounted and neither was home. This is me right now --> ](*,) It feels like i've tried everything and just haven't been able to come to a conclusion the problem. My current kernel is running fine.

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdb1       /home           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/sdb        /media/usb1     auto    rw,user,noauto  0       0
```

Thank you for anyone willing to help

---

### Post by sYs^ on 2006-04-16
I had the same problem, I bet your drive is working with the original kernel.
There's some problem between the Enterprise Volume Management System(EVMS) and your new kernel, I don't know what, but it's really annoying, I sucked a lot too with this problem. ^^
So, you will have to patch your new kernel:

1. Get the patch: ```
sudo apt-get install kernel-patch-evms
```
2. Copy the patch to your kernel's directory: ```
sudo cp /usr/src/kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch.gz /usr/src/your_kernel
```
3. Extract the patch: ```
sudo gzip -d 2.6-bd-claim.patch.gz
```
4. Apply the patch: ```
sudo cat 2.6-bd-claim.patch | patch -p1
```

Then just recompile it as usually.

It worked for me, I hope it'll for you too, Good Luck and sorry for my bad english :>

---

### Post by Union Jack on 2006-04-16
Wow, thanks so much. That did the trick :D

---

