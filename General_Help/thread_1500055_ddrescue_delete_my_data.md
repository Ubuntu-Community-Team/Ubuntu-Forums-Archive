---
title: "ddrescue delete my data"
date: 2010-06-02
forum: General Help
---

### Post by ardian923 on 2010-06-02
I tried to clone my laptop ubuntu partition (9.10) using ddrescue into my portable harddisk
I run command "ddrescue r3 /dev/sda6 /dev/sdb6"


sdb6 is my portable harddisk partition with lots of data. 
In my head I was thinking that it will create image file (like iso or img)that can be restored to another disk.
Suddenly I relize that it delete my existing data (in sdb6) then I interrupted ddrescue

Is there a way that I could get back my data in sdb6?
Partition in sdb6 is FAT32m, now when I try to open sdb6 using Windows OS, it always aks me to format

Please help...

*desperately*

---

### Post by arrange on 2010-06-02
I think the file metadata (name, location etc) are located towards the beginning of a FAT partition, so these are probably lost :(

Recovery depends on the nature of data on the partition. General tool is the *testdisk*, but there are also specialized tools for photo recovery etc.

---

### Post by ardian923 on 2010-06-02
[QUOTE=Recovery depends on the nature of data on the partition. General tool is the *testdisk*, but there are also specialized tools for photo recovery etc.[/QUOTE]

I tried teskdisk now, but it always recognize my partition as linux partition. I change type to FAT32 (0b) but I still couldn't find my previous data..:(

---

### Post by bcbc on 2010-06-02
Use photorec. It comes with testdisk.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by ardian923 on 2010-06-03
> **bcbc said:**
> Use photorec. It comes with testdisk.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Thanks bcbc , arrange,
It seems working, I guess its the time to look at those files and try to remember folder structure.

---

### Post by jerome1232 on 2010-06-03
btw the correct usage would have been

```
ddrescue /dev/sda6 /media/my_disk/sda6.img
```

pretty much never write to directly to a device like! 

I would kiss doing a nice clean recovery good by (since dd probably nuked the partition table and a portion of the fat file system)

Perhaps use'ing photorec to recover files and sort through them is your best option.

If you want to do some risky attempts I would make an image of the filesystem in it's current state. Then you could try running filesystem checks to see if you can get a working filesystem. You would always have the image to roll back to if the file system check makes things worse.

edit: huh, look at that the previous post recommended photorec, I didn't even notice it sorry.

---

### Post by ardian923 on 2010-06-03
> **jerome1232 said:**
> btw the correct usage would have been

```
ddrescue /dev/sda6 /media/my_disk/sda6.img
```



I learn something (in a hard way)...

---

