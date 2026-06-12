---
title: "dd imaging"
date: 2010-01-07
forum: General Help
---

### Post by ub007 on 2010-01-07
i'm trying to clone a hard drive using dd & netcat.
> on target:
nc -l -p 1333 |dd of=/dev/sdb

on source:
dd if=/dev/sdb |nc 192.168.0.5 1333

However after a while since the process was initiated I get a 

[B]I/O error in filesystem ("....") meta-data dev ...block 0x.....  ("xfs_read_buf") error 5 buf count 512
XFS: size check 2 failed[/B]

Further digging showed that the target hard drive was less in space by 100 kb. Both are 1 T drives seagte but different models, hence the diff in space maybe.The data on the original drive is only 900 GB. How do i get around this problem?

Cheers
David

---

### Post by amsterdamharu on 2010-01-07
Not sure if clonezilla can do it. Most imaging software do not allow for rescaling your destination partition/drive.
From [http://www.clonezilla.org/](http://www.clonezilla.org/)
"**[COLOR=#3333ff]Limitations[/COLOR]**

 
[LIST]
[*]The destination partition must be equal or larger than the source one.
[*]Differential/incremental backup is not implemented yet.
[*]Online imaging/cloning is not implemented yet. The partition to be imaged or cloned has to be unmounted.
[*]Software RAID/fake RAID is not supported by default. It's can be done manually only.
[/LIST]
"

Check out some software here:
[http://linuxappfinder.com/backupandrecovery/driveimaging](http://linuxappfinder.com/backupandrecovery/driveimaging)

If it all fails you can try do it partition for partition and dd the first 446 bytes of the last partition (only boot stuff), copy the rest of the data.

---

### Post by john newbuntu on 2010-01-07
Once the math is crunched, does anyone think using blocksize (bs) and count on the "if" side would help along with the error and notrunc option?

---

### Post by ub007 on 2010-01-07
how would the 'no trunc' option help me?

I tried using bs=256 ( same as on both disks ), but to no avail.

---

### Post by Lars Noodén on 2010-01-08
Partitioning and formatting the target disk and then using dump/restore for the transfer?

```

# on target:
cd /target
nc -l -p 1333 | restore -rf -

# on source:
time dump -f - / |nc 192.168.0.5 1333 

```

---

### Post by ub007 on 2010-01-12
question, when using rsync, does it preserve the order in which data was written on the source. to be precise does it copy data over to target in the same order as it was stored on the source?

Cheers
David

---

### Post by Lars Noodén on 2010-01-12
> **ub007 said:**
> question, when using rsync, does it preserve the order in which data was written on the source. to be precise does it copy data over to target in the same order as it was stored on the source?


I don't know the order in which rsync copies, but it copies only the changes if there are any.  It can preserve a lot of information, too

What is special about the order?

---

