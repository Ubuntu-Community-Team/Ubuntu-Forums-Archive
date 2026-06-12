---
title: "can not foramt ext3 partition completely"
date: 2010-08-23
forum: General Help
---

### Post by aboud on 2010-08-23
after several fresh format ext3/ext4/ntfs of the 200GB usb Hard, and even using gparted to delete the partition tables, and
```

dd if=/dev/zero of=/dev/sdc

```
creating a new ext3/ext4  partition leave 3 to 9 GB of used disk space. but ntfs leaves only 70M .
is this normal ? 

checking in windows and e2fsck returned no bad blocks. 

can I rely on this disk  ?

---

### Post by mscout2004 on 2010-08-23
Yes this drive is still fine so controllers dont reconize linux properly so it cant format all the drive

---

### Post by aboud on 2010-08-29
Ah .. thanks. 

but i wonder if in the future new drivers appeared for this chipset what would happen to my data, assuming I am using the disk as ext4 ?

---

### Post by sharathcshekhar on 2010-08-29
> 
creating a new ext3/ext4 partition leave 3 to 9 GB of used disk space. but ntfs leaves only 70M .
is this normal ?

Yes. This is perfectly normal. By default, when you create ext file system on linux, it reserves 5% of the disk space for root. Just in case something gets screwed and you end up consuming all this disk, this buffer space will still allow you to boot into the system. But this is useful only for your root partition and not a external HDD.
You can use tune2fs to override these settings to get that 5% usable. 
So in the terminal give the command
```

tune2fs -m 1 /dev/sdb1

```
This will reserve only 1% of the blocks in your HDD. You can even make it zero.
Maybe you'll have to check
[http://www.unixtutorial.org/commands/tune2fs/]("http://www.unixtutorial.org/commands/tune2fs/")

---

### Post by aboud on 2010-08-29
I am really grateful for the info.

---

