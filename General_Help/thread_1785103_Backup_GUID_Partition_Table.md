---
title: "Backup GUID Partition Table"
date: 2011-06-17
forum: General Help
---

### Post by bakegoodz on 2011-06-17
I know how to backup a MBR Partition table, for my specific purpose I grab entire track0 (First 32256 bytes) Command: ddrescue -s 32256 /dev/$disk track0 I know that Track 0 includes boot record, partition table, and mysterious stuff that Windows needs to boot too.

Does anyone know how bytes to copy from the start and from what I read from the end of the drive too? (I can do a reverse dd copy for that)

Thanks

Background
I'm updating a Data recovery Live CD I have worked on for a while, which I hope to release publicly soon. Unlike the others it has a menu driven scripts to automate the process. I want to add GUID support one of the tools.

---

### Post by srs5694 on 2011-06-17
The amount of data is not fixed, since GPT enables partition table sizes to vary. (Most disks support 128 partitions, but this isn't guaranteed to be true of every disk.) Your best bet is to use my [GPT fdisk (gdisk and sgdisk)](http://www.rodsbooks.com/gdisk/) to back up the data. If you're writing a script, something like this should work:

```

sgdisk -b $BACKUPFILE $SOURCEDRIVE

```

You can restore a backup with the -l option:

```

sgdisk -l $BACKUPFILE $TARGETDRIVE

```

---

### Post by bakegoodz on 2011-06-20
Thumbs up for the great answer, I'll have to include GPT Fdisk in my Project.

---

### Post by andho on 2013-02-17
Hi, will this work even with a Hybrid MBR?

---

