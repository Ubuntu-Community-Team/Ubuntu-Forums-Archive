---
title: "Disk auto-mount?"
date: 2010-01-29
forum: General Help
---

### Post by FiniteRed on 2010-01-29
Hi

What I'm sure is a basic auto-mount question here, when I plug my external USB disk into my Ubuntu server I get the following:

1) An error message saying "You are not privileged to mount this volume"

2) A window with the files on the disk open

3) A second window with all the files on the disk open

My question is why does it do it twice, and why do I get an error? - even though it still opens the drive (twice!). 

I have just added a few lines to my fstab file when the issues started but cant for the life of me see anything wrong:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=9d790309-881a-46f3-8fa7-3b0dec9a0602 /               ext3    relatime,errors=remount-ro 0       1
# /dev/md2
UUID=656e4ad5-9fb1-4d8d-a28d-9c492fa8fb0b /home           ext3    relatime        0       2
# /dev/md3
UUID=7c8a71de-69c8-4d99-8be5-bb2556d21f5a /media/Fxdata   ext3    relatime        0       2
# /dev/md1
UUID=5e3fb024-de4f-44d3-9f72-094d8fd5db54 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Dicam Duplicity disk
UUID=66a6c9c9-8163-4aa9-8d4f-5785352cf53d /home/dicam	  ext3	  defaults	  0	  0
#FxBackup Disk
UUID=2c5b54f9-9caf-4d39-b18d-1576e17096e9 /media/FxBackup ext3	  defaults	  0       0

```

There is only one partition on my USB disk...

Many thanks for any assistance you can give :D

FR

---

