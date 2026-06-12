---
title: "Partitioning a Netbook for dual booting Ubuntu and Win 7"
date: 2011-01-29
forum: General Help
---

### Post by Ron W on 2011-01-29
I'm wanting to dual boot as above and am wanting to partition the hard-drive as follows:

***
1) Windows 7

2) Storage that both Ubuntu and Win 7 can access

3) Ubuntu

I'm wanting 1) and 2) as separate primary drives and 3) as an extended drive.
***

The current drive has been partitioned at the factory as follows:

***
Volume with no name
Layout: Simple, Type: Basic, File System: <blank>, Status: Healthy(Active, Recovery Partition), Capacity: 400MB

Data (D: )
Layout: Simple, Type: Basic, File System: NTFS, Status: Healthy(Primary Partition), Capacity: 116.05GB

WINDOWS (C: )
Layout: Simple, Type: Basic, File System: NTFS, Status: Healthy(Boot, Page File, Crash Dump, Primary Partition), Capacity: 116.44GB
***

Am I unable to partition the drive as I would like because there are already three partitions on the drive?

Thanks

Ron

---

### Post by jalirious on 2011-01-29
Hi Ron, you can delete existing partitions using gparted. Your best bet seems to be resizing to three partitions, two ~7gb for the OS's, one for general storage.

I would recommend a separate home partition for ubuntu (So, four in total) - when you decided to update the ubuntu version all the files in your home dir remain unchanged.

More here; [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Ron W on 2011-01-29
I thought that it was only possible to have three partitions on a drive, 2 primary and one extended. Has that now changed?

---

### Post by Quackers on 2011-01-29
No, the maximum number of primary partitions on anyu single drive is 4. As an extended partition is a different type of primary partition, people with the need for more than 4 partitions create an extended partition as a fourth primary (in other words, they will have 3 primarys and an extended). This way they can create as many logical partitions as they want, within that extended partition.

---

### Post by TBerk on 2011-01-29
> **Ron W said:**
> I'm wanting to dual boot 
[ snip ]
The current drive has been partitioned at the factory as follows:

***
Volume with no name
Layout: Simple, Type: Basic, File System: <blank>, Status: Healthy(Active, **Recovery Partition**), Capacity: 400MB



I would be carefully deleting (for purposes of recovering HD space) this initial partition. As you stated, it is the Win7 Recovery Partition and has your MS (re)Install files on it.

As others said; you can have what you want.



In my case (XP and Ubuntu) I opted for a two partition division of labor for the Linux side of things, make that three partition division (for a total of four over all:)

- XP (dual boot using GRUB)
- linux SWAP (minimal in size, I hardly use it most of the time...)
- '\' (linux OS partition)
- '\Home' (linux home directory and the largest partition of the four by far.)


This has been a quick reply, on the fly, so to speak, ask if I'm unclear.


TBerk

---

