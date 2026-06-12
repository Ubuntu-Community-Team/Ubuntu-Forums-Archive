---
title: "How can I mount this file?"
date: 2012-01-10
forum: General Help
---

### Post by hilargi93 on 2012-01-10
Hi guys!  I need to mount this file:  
```
file image23 
image23: x86 boot sector; partition 1: ID=0x7, active, starthead 32, startsector 2048, 20967424 sectors, code offset 0xc0, OEM-ID "      &#1084;", Bytes/sector 190, sectors/cluster 124, reserved sectors 191, FATs 6, root entries 185, sectors 64514 (volumes  32 MB) , physical drive 0x7e, dos < 4.0 BootSector (0x0
```)

 I'm not sure if I can mount this file, I tried with -t vfat but launch an error. In dmesg:

```
 [742194.623557] FAT-fs (loop0): invalid media value (0xf3) 
[742194.623560] FAT-fs (loop0): Can't find a valid FAT filesystem [742451.073777] FAT-fs (loop0): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!  
```

Any help would be appreciate.  Thanks!!!

---

### Post by Mark Phelps on 2012-01-11
You don't mount "files"; you mount "filesystems".

What is it you're really trying to accomplish?

---

### Post by LewisTM on 2012-01-11
Partition ID 0x7 is NTFS.
A command like this should work
```
sudo mount -t ntfs -o loop /path/to/image23 /yourmountpoint
```

Cheers!

---

### Post by gsgleason on 2012-01-11
> **Mark Phelps said:**
> You don't mount "files"; you mount "filesystems".

What is it you're really trying to accomplish?

Not entirely accurate.

In *nix, everything is a file.  A filesystem can exist on a block device file or a regular file. 

It is absolutely possible to create a filesystem on a flat file.

Some reading for you: [http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

---

