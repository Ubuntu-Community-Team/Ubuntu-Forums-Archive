---
title: "Urgent need to increase Swap size"
date: 2009-11-10
forum: General Help
---

### Post by emigrant on 2009-11-10
hi all,
iv given a small size of swap memory (200mb) despite my ram size is 2GB.
and at the moment, i cannot do hibernation.
how can i delete sda7 and add it as swap? 
(sda7 is a partion with an older version of ubuntu which i no longer use)
[IMG]file:///tmp/moz-screenshot-2.jpg[/IMG][img]http://img203.imageshack.us/img203/3672/screenshotdevsdagpartedm.png[/img]

thank you very much for your help.


[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by Mighty_Joe on 2009-11-10
The Gparted manual is [here]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html").  
Basically, right-click on the partition you want to delete and click "delete".  I'd delete the existing swap too, then right-click on the unused space and create a new swap partition.

---

### Post by proxess on 2009-11-10
You'll also need to get that free space out of the extended area.

---

### Post by JOHNNYG713 on 2009-11-10
Hi, I would click on sda 7 and delete it then click sda 6 and delete that, then click your swap partition and resize it to the size you want, If you resize the entire amount that will give you more than enough swap space. This may take awhile, And be sure to back up ALL your important stuff before you do anything!,Home folder,bookmarks,ect. from all your partitions!

---

### Post by emigrant on 2009-11-10
did, but still get the same error.
by the way, which is my actual swap? sda3 or sda6?

[img]http://img694.imageshack.us/img694/9331/screenshotdevsdagpartedw.png[/img]

---

### Post by emigrant on 2009-11-10
btw,
in system monitor it shows the swap size as 2.4GB :(.
do i have to restart the system to make the new swap work?
[img]http://img17.imageshack.us/img17/6240/screenshotsystemmonitor.png[/img]

---

### Post by snowpine on 2009-11-10
Hi Emigrant, make sure the correct partition is listed in your /etc/fstab, here are instructions:

[https://help.ubuntu.com/community/SwapFaq#Why%20is%20my%20swap%20not%20being%20used?](https://help.ubuntu.com/community/SwapFaq#Why%20is%20my%20swap%20not%20being%20used?)

---

### Post by emigrant on 2009-11-10
everything seems ok there:

```
:~$ free
             total       used       free     shared    buffers     cached
Mem:       2061584     506500    1555084          0      28308     112436
-/+ buffers/cache:     365756    1695828
Swap:      2506048      55268    2450780

```

```
:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=becef1b2-d864-4764-828f-6381e90fd95d /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=bd49a241-1650-4369-82ae-726b389bc10c none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=2c7425b6-d64e-d288-ae82-bf2580cd63c4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by blazemore on 2009-11-10
I would just use an additional swap FILE on one of your existing partitions. There's a load of guides on how to set up a swap file in Linux, Google Is Your Friend.

Incidently, in Lucid I hear a swap file will be default?

---

### Post by renkinjutsu on 2009-11-10
> **blazemore said:**
> I would just use an additional swap FILE on one of your existing partitions. There's a load of guides on how to set up a swap file in Linux, Google Is Your Friend.

Incidently, in Lucid I hear a swap file will be default?

i don't know, but it seems like having a swap file is a step into the wrong direction. Wouldn't a swap file cause fragmentation?

@OP
what was in /dev/sda7? There was no mountpoint but all of the allocated space was used up

---

### Post by emigrant on 2009-11-10
> **renkinjutsu said:**
> 
@OP
what was in /dev/sda7? There was no mountpoint but all of the allocated space was used up

you mean in the first screenshot?
it was an old ubuntu (i think 7.10) which i no longer wanted. and i deleted and made as a swap (plz refer  the second gprated screenshot)

---

### Post by emigrant on 2009-11-12
hi all,
how can i put out sda7 from sda4? so that i can delete it and resize the swap size of sda3.
thank you very much.

---

