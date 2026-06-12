---
title: "Swap not automatically &quot;mounted&quot; after harddisc reshuffle"
date: 2011-02-03
forum: General Help
---

### Post by simon303 on 2011-02-03
I was running out of space so I added an extra harddisc (sdc) and shuffled a few mount points in /etc/fstab so it was set up how I wanted.

In the process I noticed swap was listed twice, once as /dev/sda3 and once by UUID.  While reconfiguring /etc/fstab I tried to use UUIDs so it didn't matter where the disc was physically attached so I removed the non-UUID entry and updated it to the correct UUID (for some reason it was wrong).

Now though, when I start up swap is off and I have to turn it on by the swapon command (which accepts the UUID for the swap partition.  Here is my /etc/fstab and the output of blkid

```
simon@simon-desktop:bf4390bb-39a4-43ac-ae53-d90e33062a19$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda1
UUID=1cf12d19-4c07-4665-b417-7da18bc876d8 /               ext4    relatime,errors=remount-ro 0       1

# /dev/sdb1
UUID=ccc21fd5-267b-4179-92ea-5c64e1d5d16f /home           ext4    relatime        0       2

# /dev/sdc1
UUID=e5578d50-8a82-4c9b-8558-558be4c6b53a /home/simon/Pictures  ext4    relatime    0   2

# /dev/sdc2
UUID=131204c4-2b63-4b17-a5db-9afedb927269 /home/simon/Videos    ext4    relatime    0   2

# /dev/sda2
UUID=40CC9C4ECC9C3FD8 /mnt/windows    ntfs    defaults,nls=utf8,umask=007,gid=46 0       0

# /dev/sda3
#UUID=afb21b77-fe42-48dc-ae1d-973787242a4c none            swap    sw              0       0

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

```
simon@simon-desktop:bf4390bb-39a4-43ac-ae53-d90e33062a19$ sudo blkid
/dev/sda1: UUID="1cf12d19-4c07-4665-b417-7da18bc876d8" TYPE="ext4" 
/dev/sda2: UUID="40CC9C4ECC9C3FD8" TYPE="ntfs" 
/dev/sda3: UUID="afb21b77-fe42-48dc-ae1d-973787242a4c" TYPE="swap" 
/dev/sdb1: UUID="ccc21fd5-267b-4179-92ea-5c64e1d5d16f" TYPE="ext4" 
/dev/sdd1: UUID="bf4390bb-39a4-43ac-ae53-d90e33062a19" TYPE="ext4" 
/dev/sdd2: UUID="57636376-03c4-46ab-a33e-88255448a54d" TYPE="ext4" 
/dev/sdd3: UUID="047ad586-b266-4a5d-8225-30891b961af8" TYPE="swap" 
/dev/sdc1: UUID="e5578d50-8a82-4c9b-8558-558be4c6b53a" TYPE="ext4" 
/dev/sdc2: UUID="131204c4-2b63-4b17-a5db-9afedb927269" TYPE="ext4"
```

(note: sdd is another install and is of no importance as it is often not physically attached to the computer, I mount it manually if it is ever needed)

As far as I can tell /etc/fstab is correct, but it still doesn't seem to work.

As I've already said,

```
sudo swapon -U afb21b77-fe42-48dc-ae1d-973787242a4c
```

works.

Does anyone have any idea why this is happening?  I really don't want to manually activate swap every time I start up.

---

### Post by mikewhatever on 2011-02-03
The swap line is commented out in fstab (the # symbol).

---

### Post by plucky on 2011-02-04
```
sudo blkid
/dev/sda1: UUID="1cf12d19-4c07-4665-b417-7da18bc876d8" TYPE="ext4" 
/dev/sda2: UUID="40CC9C4ECC9C3FD8" TYPE="ntfs" 
[color=blue]/dev/sda3: UUID="afb21b77-fe42-48dc-ae1d-973787242a4c" TYPE="swap"[/color]
/dev/sdb1: UUID="ccc21fd5-267b-4179-92ea-5c64e1d5d16f" TYPE="ext4" 
/dev/sdd1: UUID="bf4390bb-39a4-43ac-ae53-d90e33062a19" TYPE="ext4" 
/dev/sdd2: UUID="57636376-03c4-46ab-a33e-88255448a54d" TYPE="ext4" 
[color=blue]/dev/sdd3: UUID="047ad586-b266-4a5d-8225-30891b961af8" TYPE="swap"[/color] 
/dev/sdc1: UUID="e5578d50-8a82-4c9b-8558-558be4c6b53a" TYPE="ext4" 
/dev/sdc2: UUID="131204c4-2b63-4b17-a5db-9afedb927269" TYPE="ext4"
```

You also have two swap partitions

---

### Post by simon303 on 2011-02-04
> **mikewhatever said:**
> The swap line is commented out in fstab (the # symbol).

Ah, thanks, I feel like a bit of a fool for it being so simple.  Never mind and thank you again

> **plucky said:**
> You also have two swap partitions

Yes, but sdd is another installation and is often not even physically attached.

---

