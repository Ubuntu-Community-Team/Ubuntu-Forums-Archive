---
title: "FAT32 USB Harddrive not being seen."
date: 2010-05-02
forum: General Help
---

### Post by chrispche on 2010-05-02
I think I have a corrupted file system on my 1TB harddrive as both Windows Vista and Ubuntu are not seeing it. How do I recover the drive. I have never experienced this sort of thing before.

My suspicion is it wasn't unmounted correctly.

Please, I'm desperate that drive has all my kids pictures on it and stuff.

Thanks.

---

### Post by dino99 on 2010-05-02
vista is also on usb drive ? which distro are u talking about: lucid ?

is MountManager and usbmount and usbutils installed and prefs set ?

---

### Post by hackb0y294 on 2010-05-02
In Windows, right-click My Computer, click Manage, and click Disk Management (or click Start> Run, and type diskmgmt) Scroll down to find your USB Drive, and check to see what the filesystem is. If it says anything other than FAT32, you'll probably have to use data-recovery software to get your files back. There are plenty of free programs to do this.

---

### Post by chrispche on 2010-05-02
> **dino99 said:**
> vista is also on usb drive ? which distro are u talking about: lucid ?

is MountManager and usbmount and usbutils installed and prefs set ?

Sorry yes 10.04.

---

### Post by chrispche on 2010-05-02
> **hackb0y294 said:**
> In Windows, right-click My Computer, click Manage, and click Disk Management (or click Start> Run, and type diskmgmt) Scroll down to find your USB Drive, and check to see what the filesystem is. If it says anything other than FAT32, you'll probably have to use data-recovery software to get your files back. There are plenty of free programs to do this.

OK I did the manage thing and I can see the drive, but it'a unknown and is not assigned a drive letter. Is there anything on Ubuntu I can install to recover my data and get this working?

---

### Post by MooPi on 2010-05-02
Would you like to try a few terminal commands ?
```
sudo fdisk -l
```
```
df -h
```
We can start here an work to others after you post results

---

### Post by dino99 on 2010-05-02
> **chrispche said:**
> OK I did the manage thing and I can see the drive, but it'a unknown and is not assigned a drive letter. Is there anything on Ubuntu I can install to recover my data and get this working?

you dont give responses to my questions :(

you need to install into lucid:

ntfsprog, ntfs-3g

on windows, there is a software to read/write on ext3 too, [http://www.fs-driver.org/](http://www.fs-driver.org/) [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by MooPi on 2010-05-02
> **dino99 said:**
> you dont give responses to my questions :(

you need to install into lucid:

ntfsprog, ntfs-3g
Those utilities come standard with Lucid.

---

### Post by dino99 on 2010-05-02
> **MooPi said:**
> Those utilities come standard with Lucid.

thats why my questions into post 2

---

### Post by chrispche on 2010-05-02
> **dino99 said:**
> you dont give responses to my questions :(

you need to install into lucid:

ntfsprog, ntfs-3g

on windows, there is a software to read/write on ext3 too, [http://www.fs-driver.org/](http://www.fs-driver.org/) [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Sorry my friend it's a FAT32 HDD. I will not be able to come back to you till tonight so bare with me.

---

### Post by dino99 on 2010-05-02
> **chrispche said:**
> Sorry my friend it's a FAT32 HDD. I will not be able to come back to you till tonight so bare with me.

fat32 or ntfs = same driver

you're welcome

---

### Post by srs5694 on 2010-05-02
Please post the output of:

```

sudo fdisk -l /dev/sdb

```

Substitute the drive's ID for /dev/sdb. Please post your output inside a [noparse]```

```[/noparse] block for legibility. Chances are additional diagnostics will be required after you post this output.

---

### Post by chrispche on 2010-05-03
> **dino99 said:**
> vista is also on usb drive ? which distro are u talking about: lucid ?

is MountManager and usbmount and usbutils installed and prefs set ?

There installed now, what do I do?

---

### Post by chrispche on 2010-05-03
> **srs5694 said:**
> Please post the output of:

```

sudo fdisk -l /dev/sdb

```

Substitute the drive's ID for /dev/sdb. Please post your output inside a [noparse]```

```[/noparse] block for legibility. Chances are additional diagnostics will be required after you post this output.

There was no output.

---

### Post by chrispche on 2010-05-03
> **MooPi said:**
> Would you like to try a few terminal commands ?
```
sudo fdisk -l
```
```
df -h
```
We can start here an work to others after you post results

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008e6f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18803   151027712   83  Linux
/dev/sda2           18803       19458     5260289    5  Extended
/dev/sda5           18803       19458     5260288   82  Linux swap / Solaris
chrispche@chrispche-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  112G   24G  83% /
none                  871M  300K  871M   1% /dev
none                  878M  344K  877M   1% /dev/shm
none                  878M  288K  877M   1% /var/run
none                  878M     0  878M   0% /var/lock
none                  878M     0  878M   0% /lib/init/rw

```

---

### Post by chrispche on 2010-05-03
I think from those results we see, the drive is not there. Although in Windows Vista Manage the drive is seen. I think I'm going to need a data recovery tool. Maybe for Windows or Linux, can anyone recommend some free ones?

---

### Post by dino99 on 2010-05-03
> **chrispche said:**
> I think from those results we see, the drive is not there. Although in Windows Vista Manage the drive is seen. I think I'm going to need a data recovery tool. Maybe for Windows or Linux, can anyone recommend some free ones?

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)
[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by chrispche on 2010-05-03
Great I'll try those. Tell me something. If I quick format the drive to NTFS to restore a drive letter in Windows could I recover the data on it?

---

### Post by srs5694 on 2010-05-03
Data recovery tools will do no good if the drive isn't detected, and it looks like your drive isn't being detected. To be sure, try this:

```

ls /dev/sd? /dev/hd?

```

If the result is just "/dev/sda", with no mention of /dev/sdb or any other device file, then only one disk (your boot disk) is being detected, and your USB disk could be in the Andromeda galaxy as far as Linux is concerned.

You can do some further diagnostics by unplugging the disk, typing "dmesg | tail -20", plugging it in, waiting a few seconds, and typing "dmesg | tail -20" again. Compare the two outputs. If the kernel detects the disk, there should be some messages about that. For instance, when I plug in a USB flash drive, these are the messages it produces:

```

[3525747.203050] usb 2-4: new high speed USB device using ehci_hcd and address 32
[3525747.320237] usb 2-4: configuration #1 chosen from 1 choice
[3525747.320472] scsi35 : SCSI emulation for USB Mass Storage devices
[3525747.320729] usb-storage: device found at 32
[3525747.320731] usb-storage: waiting for device to settle before scanning
[3525752.320765] scsi 35:0:0:0: Direct-Access              USB_DRIVE        1.00 PQ: 0 ANSI: 2
[3525752.320952] sd 35:0:0:0: Attached scsi generic sg3 type 0
[3525752.321506] usb-storage: device scan complete
[3525752.322500] sd 35:0:0:0: [sdc] 31576064 512-byte logical blocks: (16.1 GB/15.0 GiB)
[3525752.322996] sd 35:0:0:0: [sdc] Write Protect is off
[3525752.322998] sd 35:0:0:0: [sdc] Mode Sense: 23 00 00 00
[3525752.323000] sd 35:0:0:0: [sdc] Assuming drive cache: write through
[3525752.325121] sd 35:0:0:0: [sdc] Assuming drive cache: write through
[3525752.325124]  sdc: sdc1 sdc2
[3525754.730523] sd 35:0:0:0: [sdc] Assuming drive cache: write through
[3525754.730527] sd 35:0:0:0: [sdc] Attached SCSI removable disk

```

This confirms that a disk device was detected and gives various technical details about its capabilities, partitions, etc. If you see *no* messages when you plug in your device, then chances are good it's just plain not there, in an electronic sense. That could mean a bad cable or other hardware fault. If you see any messages at all, it could mean there's a basic electronic connection, but some fault is preventing the device's full detection -- maybe the interface is a bit non-standard or is malfunctioning, for instance. Post what you get and somebody may be able to suggest what to do.

FWIW, I've heard that external drives' USB interfaces often fail, leaving the drives themselves perfectly functional. If this has happened, you may be able to recover your data by opening the drive's external case and either installing it as an internal drive in a computer or buying a new external case/interface.

---

### Post by chrispche on 2010-05-04
The drive is suffering from the dreaded click of death. End of the road. NO FURTHER TO GO. NEW DRIVE NEEDED. DATA LOST.

END OF THREAD.

Sorry this is very upsetting.

---

