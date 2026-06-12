---
title: "Win7(+Ubuntu) crashes after 9.10 install"
date: 2010-02-24
forum: General Help
---

### Post by Blastomorpha on 2010-02-24
I bought a new PC few months ago and tried Win7, no problems found.
Then I installed Ubuntu 9.10 for x64 (I use Ubuntu since 6.06 but until PC upgrade I sticked to 8.10) and since then, every now and then bot win and buntu crash for no reason at random, often before loggin in.
At firsth I tought it was some problems with the shared NTFS partition, so formatted it in FAT32 but this didn't helped.
Now this's my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=93cc16a6-5c70-4f05-94d2-082a90c78f18 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=d001dbbc-b070-4994-a8c1-79a0e10ecb39 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=6f6495e5-b44a-4eaf-a224-7613e3853d75 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# partizione comune linux-win FAT32
/dev/sda4       /media/sharedFAT32  vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```
A guy told me to downgrade to 9.04 because he had the same problem and that was the only way for him to deal with...

---

### Post by Blastomorpha on 2010-03-04
No one?
However, I formatted again in NTFS...

---

### Post by Kevbert on 2010-03-04
Please try running memtest86+ for a couple of passes. I'm running 9.10 and Win7 with no known problems.

---

### Post by Blastomorpha on 2010-03-08
> **Kevbert said:**
> Please try running memtest86+ for a couple of passes. I'm running 9.10 and Win7 with no known problems.

No errors after almost 3 complete passes.
At least it's not a RAM fault, maybe.

---

