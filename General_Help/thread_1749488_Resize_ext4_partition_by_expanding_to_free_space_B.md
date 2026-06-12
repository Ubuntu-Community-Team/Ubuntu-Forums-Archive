---
title: "Resize ext4 partition by expanding to free space BEFORE it"
date: 2011-05-04
forum: General Help
---

### Post by control_guy on 2011-05-04
Hello Guys

I would like to resize an ext4 partition. The drive has a chunk of free space before this partition. All the tutorials that I have read on the internet somehow implicitly assume that the partition would be expanded on the right (hence the suggestions to delete and recreate the larger partition!).

Could someone guide me on how to do that. I do not have the option to use GParted as this is a headless server, even without a graphic card. It must be done through console. Trying to partition with parted results in:
> Error: File system has an incompatible feature enabled.

 Here is some info:

```
root@dd:~# parted
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) select /dev/sdc
Using /dev/sdc
(parted) print
Model: ATA SAMSUNG HD753LJ (scsi)
Disk /dev/sdc: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size   Type     File system  Flags
 2      110GB  750GB  640GB  primary  ext4

(parted) print free
Model: ATA SAMSUNG HD753LJ (scsi)
Disk /dev/sdc: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
        32.3kB  110GB  110GB            Free Space
 2      110GB   750GB  640GB   primary  ext4
        750GB   750GB  2613kB           Free Space


```

As you can see, I would like to merge the 110GB free block to the partition no. 2.

Thanks.

---

### Post by control_guy on 2011-05-06
Anyone?

---

