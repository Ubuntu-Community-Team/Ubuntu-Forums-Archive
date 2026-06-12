---
title: "Unable to mount a GPT HFS+ partition"
date: 2012-06-14
forum: General Help
---

### Post by leth on 2012-06-14
I have a drive attached that was pulled from an iMac and I'm trying to recover some data off it.  I've mounted other HFS+ partitions before so I'm not sure why this one is giving me trouble.  Here's what's happening:

```

# fdisk -l /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   312581800   156290900   ee  GPT

```Ok, so it's using GPT ...

```

# parted /dev/sdb print
Model: WDC WD16 00JS-40TGB0 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      20.5kB  210MB  210MB  fat32        EFI System Partition  boot
 2      210MB   160GB  160GB  hfs+         Customer


```I can see the GPT partitions.  No problem so far.  But when I try to mount it:

```

# mount -t hfsplus -o force /dev/sdb2 /tmp/mac
mount: special device /dev/sdb2 does not exist

```Hmm.  So then I checked  /dev:

```

# ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb

```How come /dev/sdb1 and sdb2 don't exist?

Is there something special I need to do to mount a GPT partition?

I am running Ubuntu 12.04.

Any help is appreciated.  Thanks.

---

### Post by newpreludeking on 2012-09-03
Hi

I am also greeting the same error

I am not able to mount the drive.

Can any one help me please?

Thanks

---

### Post by leth on 2012-09-03
I never found a real solution for this.   I ended up using my GF's iMac to recover files off the drive, and it had no issues so it wasn't like the drive was corrupt. 

The weird part is I was able to mount a different HFS drive with Ubuntu and had no issues.

---

