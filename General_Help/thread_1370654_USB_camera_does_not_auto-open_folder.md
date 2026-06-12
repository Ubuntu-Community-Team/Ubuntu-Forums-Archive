---
title: "USB camera does not auto-open folder"
date: 2010-01-02
forum: General Help
---

### Post by Kschikan on 2010-01-02
I'm having trouble getting my USB camera to auto open a folder when I plug it in after I upgraded from 9.04 to 9.10.

The camera is a Olympus Optical C-740

I checked my configuration settings in gconf-editor and checked /apps/nautilus/preferences/media_automount and /apps/nautilus/preferences/media_automount_open. Both were checked. 

From nautilus, going to Edit->Preferences->Media has "Open folder" selected for pictures, and "ask me what to do" for all the others. 

As per [http://www.uluga.ubuntuforums.org/showthread.php?t=1306577]("http://www.uluga.ubuntuforums.org/showthread.php?t=1306577") I tried installing gnome-mount and gnome-volume-manager but both were already installed and up to date. 

I tried following the instructions at [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) to no avail.

Output of lsusb is 
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 07b4:0105 Olympus Optical Co., Ltd Camedia C-310Z/C-700/C-750UZ/C-755/C-765UZ/C-3040/C-4000/C-5050Z/D-560/C-3020Z Zoom Camera
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

output of sudo fdisk -l is 

```

Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcb1ec06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10445    83899431    7  HPFS/NTFS
/dev/sda2           10446       14419    31921155   83  Linux
/dev/sda3           14420       14596     1421752+   5  Extended
/dev/sda5           14420       14596     1421721   82  Linux swap / Solaris

```

Output from dmesg from when I plug the camera in until I remove it is:

```
[13633.780027] usb 4-1: new full speed USB device using uhci_hcd and address 3
[13633.967107] usb 4-1: configuration #1 chosen from 1 choice
[13633.970268] scsi3 : SCSI emulation for USB Mass Storage devices
[13633.970481] usb-storage: device found at 3
[13633.970485] usb-storage: waiting for device to settle before scanning
[13638.969199] usb-storage: device scan complete
[13638.972200] scsi 3:0:0:0: Direct-Access     OLYMPUS  C740UZ           1.00 PQ: 0 ANSI: 2
[13638.972757] sd 3:0:0:0: Attached scsi generic sg1 type 0
[13638.984362] sd 3:0:0:0: [sdb] 33554432 512-byte logical blocks: (17.1 GB/16.0 GiB)
[13638.988655] sd 3:0:0:0: [sdb] Write Protect is off
[13638.988662] sd 3:0:0:0: [sdb] Mode Sense: 18 00 00 08
[13638.988666] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[13639.009199] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[13639.009210]  sdb: sdb1
[13639.038465] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[13639.038476] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[13639.380032] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[13672.112037] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[13682.384027] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[13698.660037] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[13698.936034] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[13709.208032] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[13709.370390] sd 3:0:0:0: Device offlined - not ready after error recovery
[13709.370406] sd 3:0:0:0: [sdb] Unhandled error code
[13709.370410] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[13709.370415] end_request: I/O error, dev sdb, sector 33554304
[13709.370423] Buffer I/O error on device sdb, logical block 4194288
[13709.370471] sd 3:0:0:0: rejecting I/O to offline device
[13709.370530] sd 3:0:0:0: rejecting I/O to offline device
[13709.370542] sd 3:0:0:0: rejecting I/O to offline device
[13709.370577] sd 3:0:0:0: rejecting I/O to offline device
[13709.370588] sd 3:0:0:0: rejecting I/O to offline device
[13709.370602] sd 3:0:0:0: rejecting I/O to offline device
[13709.370616] sd 3:0:0:0: rejecting I/O to offline device
[13709.370630] sd 3:0:0:0: rejecting I/O to offline device
[13709.370646] sd 3:0:0:0: rejecting I/O to offline device
[13709.370660] sd 3:0:0:0: rejecting I/O to offline device
[13709.370681] sd 3:0:0:0: rejecting I/O to offline device
[13709.370699] sd 3:0:0:0: rejecting I/O to offline device
[13709.370714] sd 3:0:0:0: rejecting I/O to offline device
[13709.370728] sd 3:0:0:0: rejecting I/O to offline device
[13709.370758] sd 3:0:0:0: rejecting I/O to offline device
[13709.370772] sd 3:0:0:0: rejecting I/O to offline device
[13709.370795] sd 3:0:0:0: rejecting I/O to offline device
[14918.112075] usb 4-1: USB disconnect, address 3

```


Any Ideas? Thanks in advance.

So the camera seems to be recognized and mounted but

---

### Post by grgzfla on 2010-01-09
I have an older Olympus D-560 which my daughter uses, and am running into the same problem.  'lsusb' can identify the camera on the usb chain, but I'm not able to access the CDIM folder.  'fdisk -l' doesn't report it in /dev.

I have other USB drives that automatically mount without a problem.

Solutions, hints or ideas anyone?  :confused:

---

### Post by guybrush.d on 2010-01-29
Hi guys,
i've a similar problem after struggling with my sister, that asked me every to reinstall windows xp on her
laptop because of viruses, i bulldozed her to learn and use ubuntu! ;)

i installed ubuntu studio 9.04 because she liked the windows decoration, everything went
fine but when i tried to install digikam for her Olympus FE-250 the problems, same of yours, began! :(

i goggled a bit and i found these links:

[http://www.teaser.fr/~hfiguiere/linux/digicam.html#olym-specifics]("http://www.teaser.fr/%7Ehfiguiere/linux/digicam.html#olym-specifics")

[http://fudoshin.wordpress.com/2008/03/27/resolved-camera-mount-problem/](http://fudoshin.wordpress.com/2008/03/27/resolved-camera-mount-problem/)

[http://forum.ubuntu-it.org/index.php/topic,285221.0.html](http://forum.ubuntu-it.org/index.php/topic,285221.0.html)

[http://www.faqs.org/docs/Linux-HOWTO/USB-Digital-Camera-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/USB-Digital-Camera-HOWTO.html)

i didn't try them yet, but maybe it can help you! (I HOPE SO)

CIAO

---

