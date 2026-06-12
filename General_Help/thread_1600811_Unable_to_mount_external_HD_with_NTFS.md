---
title: "Unable to mount external HD with NTFS"
date: 2010-10-19
forum: General Help
---

### Post by Setya on 2010-10-19
Hi all,

I have an old external 20GB HD formatted with NTFS. It used to be able to mount in Ubuntu just fine. 

One day I copied a huge file into it, then suddenly it failed to mount. Initially the message was something like the following:

```

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

After several failed attempts to rescue the content using ddrescue, now I can not see /dev/sdb partition at all.

Here's the result of fdisk -l command:

```

setya@promisedlander:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7a2e7a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2249    18065061   83  Linux
/dev/sda2            2250       14593    99153180    5  Extended
/dev/sda5            2250        4802    20506941   82  Linux swap / Solaris
/dev/sda6            4803       14593    78646176   83  Linux

```

As you can see the above list doesn't contain /dev/sdb. But when I plug the external HD, the connection light always turns green.

If possible I want to save the data in it, if not I just want to reformatted into NTFS again.

Any help would be greatly appreciated.

Best Regards,

Setya

---

### Post by Mark Phelps on 2010-10-19
The conventions of /sda, /sdb ... refer to entire physical drives, not to partitions.

So, if you have entries for /sdan (n being a number) and for  /sdbn (n being a number), you have two physical drives, each with their own set of partitions.

If you're no longer seeing /sdb at all, your OS is not seeing the drive.

---

### Post by sikander3786 on 2010-10-19
As **Mark** suggested above, your OS is not seeing the entire drive and the reason might be

> or there is a hardware fault

from the initial error message.

Can you check on some other system/OS if it mounts there?

---

### Post by blueridgedog on 2010-10-19
Connect the drive to a system running windows and determine if it is visible, then as instructed, run chkdsk /f from within windows on the drive.

---

### Post by gamesbook on 2010-10-20
I have exactly the same problem - when I try and run the chkdsk, Windows tells that that command is not supported ...

---

### Post by Setya on 2010-10-20
Hi,

For what it's worth, here the message from /var/log/messages when I plug the HD:
```

Oct 20 14:39:29 promisedlander kernel: [16173.240135] usb 3-1: new full speed USB device using uhci_hcd and address 18
Oct 20 14:39:30 promisedlander kernel: [16173.804054] usb 3-1: new full speed USB device using uhci_hcd and address 19
Oct 20 14:39:31 promisedlander kernel: [16174.328046] usb 3-1: new full speed USB device using uhci_hcd and address 20
Oct 20 14:50:11 promisedlander -- MARK --
Oct 20 15:10:11 promisedlander -- MARK --
Oct 20 15:30:11 promisedlander -- MARK --
Oct 20 15:50:11 promisedlander -- MARK --
Oct 20 16:10:11 promisedlander -- MARK --
Oct 20 16:30:11 promisedlander -- MARK --
Oct 20 16:50:11 promisedlander -- MARK --
Oct 20 16:52:22 promisedlander kernel: [24145.536125] usb 1-3: new high speed USB device using ehci_hcd and address 56
Oct 20 16:52:22 promisedlander kernel: [24145.808934] usb 1-3: configuration #1 chosen from 1 choice
Oct 20 16:52:22 promisedlander kernel: [24145.809407] scsi19 : SCSI emulation for USB Mass Storage devices
Oct 20 16:52:27 promisedlander kernel: [24150.843830] scsi 19:0:0:0: Direct-Access     ST92011A                  3.07 PQ: 0 ANSI: 0
Oct 20 16:52:27 promisedlander kernel: [24150.846608] sd 19:0:0:0: [sdb] 39070080 512-byte hardware sectors: (20.0 GB/18.6 GiB)
Oct 20 16:52:27 promisedlander kernel: [24150.847600] sd 19:0:0:0: [sdb] Write Protect is off
Oct 20 16:52:27 promisedlander kernel: [24150.849733] sd 19:0:0:0: [sdb] 39070080 512-byte hardware sectors: (20.0 GB/18.6 GiB)
Oct 20 16:52:27 promisedlander kernel: [24150.862394] sd 19:0:0:0: [sdb] Write Protect is off
Oct 20 16:52:27 promisedlander kernel: [24150.862439]  sdb: sdb1
Oct 20 16:52:27 promisedlander kernel: [24151.197713] sd 19:0:0:0: [sdb] Attached SCSI disk
Oct 20 16:52:27 promisedlander kernel: [24151.197860] sd 19:0:0:0: Attached scsi generic sg2 type 0
Oct 20 16:53:07 promisedlander kernel: [24191.112098] usb 1-3: reset high speed USB device using ehci_hcd and address 56
Oct 20 16:53:13 promisedlander kernel: [24196.676098] usb 1-3: reset high speed USB device using ehci_hcd and address 56
Oct 20 16:53:13 promisedlander kernel: [24197.244128] usb 1-3: reset high speed USB device using ehci_hcd and address 56
Oct 20 16:53:14 promisedlander kernel: [24197.776135] usb 1-3: reset high speed USB device using ehci_hcd and address 56
Oct 20 16:53:14 promisedlander kernel: [24198.197293] sd 19:0:0:0: Device offlined - not ready after error recovery
Oct 20 16:53:14 promisedlander kernel: [24198.197331] sd 19:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 20 16:53:14 promisedlander kernel: [24198.197350] __ratelimit: 388 callbacks suppressed
Oct 20 16:53:14 promisedlander kernel: [24198.199947] usb 1-3: USB disconnect, address 56
Oct 20 16:53:14 promisedlander kernel: [24198.200052] sd 19:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 20 16:53:15 promisedlander kernel: [24198.324057] usb 1-3: new high speed USB device using ehci_hcd and address 57
Oct 20 16:53:15 promisedlander kernel: [24198.888156] usb 1-3: new high speed USB device using ehci_hcd and address 58
Oct 20 16:53:16 promisedlander kernel: [24199.456226] usb 1-3: new high speed USB device using ehci_hcd and address 59
Oct 20 16:53:16 promisedlander kernel: [24199.984136] usb 1-3: new high speed USB device using ehci_hcd and address 60
Oct 20 16:53:17 promisedlander kernel: [24200.668101] usb 3-1: new full speed USB device using uhci_hcd and address 21
Oct 20 16:53:17 promisedlander kernel: [24201.228072] usb 3-1: new full speed USB device using uhci_hcd and address 22
Oct 20 16:53:18 promisedlander kernel: [24201.788123] usb 3-1: new full speed USB device using uhci_hcd and address 23
Oct 20 16:53:19 promisedlander kernel: [24202.308056] usb 3-1: new full speed USB device using uhci_hcd and address 24

```

On Windows when I plug the external HD, a message box asking to format the drive pop up, but when I click OK, it says that it can not format the HD.

but when I try to chkdsk, it says:
```

The type of the file system is RAW
chkdsk is not available for RAW drives.

```

Thanks & Regards,

Setya

---

### Post by Mark Phelps on 2010-10-20
[QUOTE=Setya;9999963]
```

The type of the file system is RAW
chkdsk is not available for RAW drives.

```

That's really BAD news.  Means you drive has no partitions on it or the existing partition table is corrupted so badly that neither MS Windows nor Ubuntu can make sense out of it.

Your only hope is to run data recovery software against that drive after plugging it into another machine as an external drive.

If you have an MS Windows box, I have had really good results using apps from Runtime Software: GetDataBack for NTFS and Recovery My Files.  You can download free trials from their website.

But, you'll need an MS Windows PC to install them, and while you can run them to see how well they detect the drive and the files on it, you will have to purchase them to do the actual data recovery.

Your data ... your money ... your choice.

---

### Post by blueridgedog on 2010-10-20
testdisk under Ubuntu can also take a swing at getting files off of the drive.  If you simply want to repartition it, you can do that using the disk management tool in windows (right click my computer, select manage, then disk and storage) or gparted.

---

