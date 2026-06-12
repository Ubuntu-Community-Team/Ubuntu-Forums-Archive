---
title: "Created ext2 partition but blkid still reports as vfat"
date: 2010-11-19
forum: General Help
---

### Post by Cool Javelin on 2010-11-19
I had a 40G vfat drive from WIN98 and I used parted to remove the partition, then create a new partition with an ext2 filetype

When in parted, and do print...

```

(parted) p
Model: ATA QUANTUM FIREBALL (scsi)
Disk /dev/sdd: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.0GB  40.0GB  primary  ext2

```

Why is the the Partition Table shown as msdos?

Also, here is the output of blkid: 

```

mark@Legolas:/etc$ blkid
/dev/sda1: UUID="d52de253-ae12-424a-9d99-1a62d26bbb6a" TYPE="ext2"
/dev/sda5: UUID="0904af52-f584-4fd2-a045-760959670db3" TYPE="swap"
/dev/sdb1: UUID="963e3bdb-d3e6-4ac8-a775-a9c146783541" TYPE="ext2"
/dev/sdc: UUID="bc5827f5-5fd6-41a0-a96a-ad97a8bd6158" TYPE="ext2"
/dev/sdd1: LABEL="HMATO_D 37G" UUID="135B-16DE" TYPE="vfat"
/dev/sde1: UUID="a7e7a390-77a2-4467-82eb-3cce977c05d8" TYPE="ext2"

```

Note sdd1 still shows as vfat, with a 8 character UUID. Why?

Thanks for your help,
Mark.

---

### Post by dino99 on 2010-11-19
is that hdd tatooed ? with gparted can you see sdd1 ?

[http://ohioloco.ubuntuforums.org/showpost.php?p=8942653&postcount=7](http://ohioloco.ubuntuforums.org/showpost.php?p=8942653&postcount=7)

---

### Post by plucky on 2010-11-19
> **Cool Javelin said:**
> I had a 40G vfat drive from WIN98 and I used parted to remove the partition, then create a new partition with an ext2 filetype

When in parted, and do print...

```

(parted) p
Model: ATA QUANTUM FIREBALL (scsi)
Disk /dev/sdd: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.0GB  40.0GB  primary  ext2

```

Why is the the Partition Table shown as msdos?

Also, here is the output of blkid: 

```

mark@Legolas:/etc$ blkid
/dev/sda1: UUID="d52de253-ae12-424a-9d99-1a62d26bbb6a" TYPE="ext2"
/dev/sda5: UUID="0904af52-f584-4fd2-a045-760959670db3" TYPE="swap"
/dev/sdb1: UUID="963e3bdb-d3e6-4ac8-a775-a9c146783541" TYPE="ext2"
/dev/sdc: UUID="bc5827f5-5fd6-41a0-a96a-ad97a8bd6158" TYPE="ext2"
/dev/sdd1: LABEL="HMATO_D 37G" UUID="135B-16DE" TYPE="vfat"
/dev/sde1: UUID="a7e7a390-77a2-4467-82eb-3cce977c05d8" TYPE="ext2"

```

Note sdd1 still shows as vfat, with a 8 character UUID. Why?

Thanks for your help,
Mark.

The blkid command reads the information saved in a file.

Try ```
sudo blkid
``` which updates the file that blkid reads.

Good luck

---

### Post by Cool Javelin on 2010-11-19
plucky:

Thanks, that worked;

mark@Legolas:~$ sudo blkid
[sudo] password for mark:
/dev/sda1: UUID="d52de253-ae12-424a-9d99-1a62d26bbb6a" TYPE="ext2"
/dev/sda5: UUID="0904af52-f584-4fd2-a045-760959670db3" TYPE="swap"
/dev/sdb1: UUID="963e3bdb-d3e6-4ac8-a775-a9c146783541" TYPE="ext2"
/dev/sdc: UUID="bc5827f5-5fd6-41a0-a96a-ad97a8bd6158" TYPE="ext2"
/dev/sde1: UUID="a7e7a390-77a2-4467-82eb-3cce977c05d8" TYPE="ext2"
/dev/sdd1: UUID="a1d94017-db8d-4ce5-a6ac-bbc27ad33dcd" TYPE="ext2"
mark@Legolas:~$

But parted still shows... (note the msdos reference below)

Using /dev/sdd
(parted) p
Model: ATA QUANTUM FIREBALL (scsi)
Disk /dev/sdd: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.0GB  40.0GB  primary  ext2

(parted)

To be honest, I guess I don't care, from now on I am just wondering why.

Mark.

---

### Post by plucky on 2010-11-19
From Gparted Help file 
```
1. Select a disk device. See Section 4.1 &#8213; Selecting a Device.
              
2. Choose:        Device &#9656; Create Partition Table.
                  The application displays a
                  Create partition table on /path-to-device
                  dialog.

3.                [color=red]If you want a partition table other than msdos,[/color] click
                  Advanced and select a partition table type
                  from the list.

4.                Click Apply to create the new partition table.
                  The application writes the new partition table to 
                  the disk device.
                  The application refreshes the device 
                  partition layout in the gparted window.

```

---

### Post by Cool Javelin on 2010-11-19
dino99:

I am sorry, I didn't see your reply before, my bad.

I don't understand what you mean by "tatooed". I did go to the link you have, I guess the dd thing is to replicate from another drive that doesn't have these issues.

Not too sure it applies here.

I don't have a graphical interface, no "X", so I can't use gparted, I am stuck with only parted. Is there a third text only partition editor I can use that may be more sophisticated?

plucky:

I will look into these suggestions, it is feeding me more information. I guess the file system within the partition can be different then the partition type.

I seem to recall there being one byte in the partition table that says it's type, I thought parted set that byte.

You have both given me some more info, I can start to search for more now that I know what to search for.

Maybe I should use the liveCD and use gparted to fix this one.

I started using the drive, I will need to move the data off it first in case I hose it.

Thanks,
Mark.

---

### Post by santosh83 on 2010-11-19
> **Cool Javelin said:**
> plucky:

Thanks, that worked;

mark@Legolas:~$ sudo blkid
[sudo] password for mark:
/dev/sda1: UUID="d52de253-ae12-424a-9d99-1a62d26bbb6a" TYPE="ext2"
/dev/sda5: UUID="0904af52-f584-4fd2-a045-760959670db3" TYPE="swap"
/dev/sdb1: UUID="963e3bdb-d3e6-4ac8-a775-a9c146783541" TYPE="ext2"
/dev/sdc: UUID="bc5827f5-5fd6-41a0-a96a-ad97a8bd6158" TYPE="ext2"
/dev/sde1: UUID="a7e7a390-77a2-4467-82eb-3cce977c05d8" TYPE="ext2"
/dev/sdd1: UUID="a1d94017-db8d-4ce5-a6ac-bbc27ad33dcd" TYPE="ext2"
mark@Legolas:~$

But parted still shows... (note the msdos reference below)

Using /dev/sdd
(parted) p
Model: ATA QUANTUM FIREBALL (scsi)
Disk /dev/sdd: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.0GB  40.0GB  primary  ext2

(parted)

To be honest, I guess I don't care, from now on I am just wondering why.

Mark.

It's pretty standard for PCs to use the MS-DOS partition table (because DOS first used & later OSes stuck with it for compatibility I guess), but that's only the format of the MBR. The individual partitions can still be of any filesystem type. If you use a partition table type other than DOS, then Windows systems may not be able to boot.

---

### Post by Cool Javelin on 2010-11-19
santosh83:

Thanks for the reply.

I am not worried about booting windows systems on this machine, but I am thinking of leaving this particular issue alone. The system seems to be stable (other then me poking around and tossing a wrench from time to time.)  :)

Mark.

---

