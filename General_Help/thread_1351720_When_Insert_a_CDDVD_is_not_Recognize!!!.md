---
title: "When Insert a CD/DVD is not Recognize!!!"
date: 2009-12-10
forum: General Help
---

### Post by lrcaballero on 2009-12-10
Hi everyone!

Whenever I put a cd/dvd into the cd-rom/dvd-rom ubuntu is not recognizing it!! but if I restart my laptop then it appears. What can I do so that it recognizes cd/dvd's when I put them in the drive???? Thank you.

Luis

---

### Post by lrcaballero on 2009-12-10
can any one help please!!!

---

### Post by john newbuntu on 2009-12-10
OPen a terminal and type:
```
sudo mount /dev/cdrom
```

See if that recognizes the drive.  If not, please run this command and past the output:
```
cat /etc/fstab
```

---

### Post by romina17 on 2010-02-01
Hi! I have the same problem..
My driver isn't recognized
Here I paste the output:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=efcb664c-5aeb-4d64-803b-450a1cd550af /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d335b949-216f-4a28-952c-37f1215658af none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Thanks!!!

---

