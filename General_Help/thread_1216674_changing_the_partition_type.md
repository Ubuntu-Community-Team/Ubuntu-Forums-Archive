---
title: "changing the partition type"
date: 2009-07-18
forum: General Help
---

### Post by GBLinux on 2009-07-18
Hello guys,

I had a NTFS based where i had lot's of data in it.
But accidently while in the process of installation of ubuntu it got converted into swap drive because of my mistake.The drive size is same as of previous and the data is still there.

Now actually i want to convert the drive file system type to "HPFS - NTFS" by "testdrive" software and the answer i want to know is -

1. Will the data be lost ?
2. How do i recover the data without changing the file system

Thank You!

---

### Post by unutbu on 2009-07-18
[COLOR="Red"]Boot from a LiveCD. You do not want Linux using your NTFS partition as swap![/COLOR]

To change the partition type to NTFS you can use a command like this:
```

sudo sfdisk --change-id /dev/sdb 5 7

```
Note that this changes the partition type of /dev/sdb5 to HPFS/NTFS.

You'll have to change "sdb" and 5 in the above command to whatever is appropriate for your machine.

The sfdisk command above is safe. No data will be lost because of it, and the change is revertable.

If uncertain of exactly how to adapt the sfdisk command to your situation, open a terminal (Applications>Accessories>Terminal) and post the output of 
```

sudo fdisk -l
```

("-l" is a minus lowercase L). This will show us your partition table.

---

