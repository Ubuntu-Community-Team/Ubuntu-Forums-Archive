---
title: "HDD Busy Error, wont mount."
date: 2010-12-04
forum: General Help
---

### Post by Alycan on 2010-12-04
Lately my second HDD won't mount anymore. It always states that it is Busy. And wel I need the data on it so formatting isn't an option for me so could anyone help me?

```

root@usr-desktop:/home/usr# sudo mount /dev/sda /media/Algemeen -o force
mount: /dev/sda already mounted or /media/Algemeen busy
```

SOLVED: Thread can be marked solved, Motherboard failure / Cable Replacement.

---

### Post by dandnsmith on 2010-12-04
As stated, the problem may be obvious - the device quoted is **/dev/sda**, but, as an HDD it must have a partition table and at least one partition, so it may well be **/dev/sda1**

Apart from that use *sudo mount*, and *sudo fdisk -l* to find out about the disk properties.

Having said that, as the **2nd HDD** it should be **sdb**

---

### Post by Alycan on 2010-12-04
> **dandnsmith said:**
> As stated, the problem may be obvious - the device quoted is **/dev/sda**, but, as an HDD it must have a partition table and at least one partition, so it may well be **/dev/sda1**

Apart from that use *sudo mount*, and *sudo fdisk -l* to find out about the disk properties.

Having said that, as the **2nd HDD** it should be **sdb**

What part didn't you understand that those command's wont work?  And being all witty about the 2nd HDD should be sdb isn't really called contributing now is it.

BTW: I have also tried sda**1** so no sweat I actually am past that point already.

---

### Post by dandnsmith on 2010-12-05
I think you really didn't take in what I was saying - probably because you were feeling frustrated.

I wasn't suggesting trying to mount the HDD, but to use mount to find whether it was shown as mounted elsewhere already.

The bit about the device names was also well meant - using fdisk might (from it's display) show which disk name was actually required.

I'm chary about saying anything more, as it, too, might be taken amiss

Hope you succeed in your quest.

---

### Post by Alycan on 2010-12-05
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38914   312571223+  ee  GPT

```The outcome of fdisk.

```
 can't find /dev/sda1 in /etc/fstab or /etc/mtab
```

Outcome of sudo mount.

---

### Post by srs5694 on 2010-12-05
Your disk uses the GUID Partition Table (GPT) scheme, rather than the more common Master Boot Record (MBR) scheme, so fdisk is useless. Instead, please post the output of "sudo parted /dev/sda print" and of "sudo parted /dev/sdb print".

I'm skeptical that the second command will work, since fdisk doesn't seem to have reported anything for /dev/sdb. In fact, it appears that you don't have a second hard disk. If you believe otherwise, please post details about what this disk is and how it differs from your first. (Is the second disk internal or external? If the latter, what type of interface does it use?) You could also try posting the output of "dmesg | grep sdb" from soon after you boot.

---

### Post by Alycan on 2010-12-06
```
Model: ATA WDC WD3200AAKS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      17.4kB  320GB  320GB  ext4

``````
Model: ATA ST3200822AS (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  197GB  197GB   primary   ext4
 2      197GB   200GB  3144MB  extended
 5      197GB   200GB  3144MB  logical   linux-swap(v1)

```Both internal utilizing SATA.

Edit:
Weird, it just mounted didn't change any settings at all. Seems to work like normal tho..

---

### Post by srs5694 on 2010-12-06
FWIW, your second drive uses MBR partitions.

Since this error now seems intermittent, I'd start running hardware diagnostics. Look over the disks' SMART status using any of several SMART monitoring tools. Perhaps one of them is failing. It's also possible you've got a loose or damaged cable that's causing the drive to disappear or appear to be busy from time to time.

---

### Post by Alycan on 2010-12-06
Motherboard is failing yes, 8 year old hardware :-# anyway thx for the help provided already changed the cable. Disk appears healthy when running diagnostics.

Motherboard and graphics card are an different story though.

---

