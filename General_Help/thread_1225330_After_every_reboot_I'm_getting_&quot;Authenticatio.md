---
title: "After every reboot I'm getting &quot;Authentication is required to mount device&quot;"
date: 2009-07-28
forum: General Help
---

### Post by andresmh on 2009-07-28
This is what I am getting:

[[IMG]http://img196.imageshack.us/img196/6445/screenshot1f.th.png[/IMG]](http://img196.imageshack.us/my.php?image=screenshot1f.png)

I think it might be the Windows partition but I am not sure.
In any case, I don't seem to have that partition listed in fstab:

```

$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=e6e8ef1b-5e44-4d5c-b28a-7afbf11f009f /               ext4    relatime,errors=remount-ro 0       1
# /docs was on /dev/sda5 during installation
UUID=7ccfaf0c-7abf-470d-9a68-56b3b1cc3cf1 /docs           ext3    relatime        0       2
# /home was on /dev/sda7 during installation
UUID=09666c20-a671-4074-a391-7531b113c31a /home           ext4    relatime        0       2
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

Any ideas?

---

### Post by philinux on 2009-07-28
If you're running karmic then this is currently a reported bug. Current advice is just click cancel.

Correct forum to post is...
[Karmic]("http://ubuntuforums.org/forumdisplay.php?f=359")

This is a development version still only at alpha3. Not due to be released till October.

---

### Post by VMC on 2009-08-03
> **philinux said:**
> If you're running karmic then this is currently a reported bug. Current advice is just click cancel.

Correct forum to post is...
[Karmic]("http://ubuntuforums.org/forumdisplay.php?f=359")

This is a development version still only at alpha3. Not due to be released till October.

Yes your right. It is in Karmic, but I can't find any info on that bug. I googled but found nothing. Searched Karmic forum, still nothing. Thanks.

---

### Post by softwareregisterac on 2009-08-04
Hi All,

Plz download 

sudo apt-get install pysdm

choose your device and mount your partitions accordingly.

This should solve your problem

Thanks

---

### Post by bacardiandwatermelon on 2009-08-11
> **VMC said:**
> Yes your right. It is in Karmic, but I can't find any info on that bug. I googled but found nothing. Searched Karmic forum, still nothing. Thanks.

I think these are the bugs..
[https://bugs.launchpad.net/ubuntu/karmic/+source/devicekit-disks/+bug/409216](https://bugs.launchpad.net/ubuntu/karmic/+source/devicekit-disks/+bug/409216)
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/403976](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/403976)

Oh and pysdm worked for me, they still mount.. But they won't ask you for authentication....

---

### Post by LuckyLucke on 2010-03-01
i resolved the problem like this:

first go to:

System->Administration->Storage Device Manager 

on the left side (Partition List) choose your partition and click 'Mount' button

that's all there!

Have fun!

---

### Post by JEREMIAHBARLOW on 2010-05-06
> **LuckyLucke said:**
> i resolved the problem like this:

first go to:

System->Administration->Storage Device Manager 

on the left side (Partition List) choose your partition and click 'Mount' button

that's all there!

Have fun!


**L** labor
**U** under
**C** correct
**K** knowledge

Lucky, thank you so much for that tip.  That worked great for mounting and remounting FAT and NTFS partitions automatically after reboot.

;)

---

