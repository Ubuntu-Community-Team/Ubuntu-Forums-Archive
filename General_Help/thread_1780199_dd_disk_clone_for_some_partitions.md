---
title: "dd disk clone for some partitions"
date: 2011-06-11
forum: General Help
---

### Post by conradin on 2011-06-11
Hello Ubuntu Forum users!!
I have a 160Gb Hard drive with 3 partitions. sda1, sda2, sda3.
sda1 & 2 are just under 20 GB each. the other 120 GB is free space.
I have sooo many 40GB hard drives! I would like to copy (with dd) the MBR, sda1 & 2 to a 40GB hard drive and be able to just use that so I can free up my 160GB hard drives. 

Typically when I want to clone something, the drives are equal or larger than the original. I'm not too sure about this, and if I use code (show below), will I also get the MBR?

#where sda is the 160gb with 3 partitions and drive sdb is a 40GB drive with 2 partitions.
```


dd if=/dev/sda1 of=sdb1
dd if=/dev/sda1 of=sdb1

```
 Also, is there a way i can do this with 1 line, or have both dd operations running simultaneously?

---

### Post by dabl on 2011-06-11
I would advise making a careful study of dd, before using it -- it is powerful, but totally unforgiving of errors.

That said, AFAIK the target partition MUST be equal (to the byte) or larger than the source partition, or the command will fail.

I happen to know (thanks to oshunluvr) how to use dd just to make a backup copy of an mbr:

1. Open a terminal window
2. Type  sudo dd if=/dev/sda of=mbrsave.bin bs=512 count=1
3. Type  sudo chown YOURUSERNAME:YOURPRIMARYGROUPNAME mbrsave.bin
4. Copy this file to a safe location not on your computer. i.e. usbdisk, email it to your gmail address, floppy disc, cdrom, whatever.

Here is dd guidance:  [http://kubuntuforums.net/forums/index.php?topic=3117215.0](http://kubuntuforums.net/forums/index.php?topic=3117215.0)

---

### Post by psusi on 2011-06-11
I would suggest that you reinstall using LVM.  With LVM you can easily move partitions around or split them across multiple disks, all without having to unmount them or reboot.  See [http://wiki.ubuntu.com/Lvm](http://wiki.ubuntu.com/Lvm).

To answer your question, sda1 is the partition.  The MBR is the first sector of the raw disk, sda.

---

