---
title: "USB Drive in External Enclosure Not Auto Mounted or Seen from Device Notifier.."
date: 2009-07-07
forum: General Help
---

### Post by killabee44 on 2009-07-07
Hi all,

I have a 400 GB drive in an external enclosure (Venus DS5), that Kubuntu will not see from the device notifier. I cannot see it from dolphin either. 

I know kubuntu does see it because when I do a: 

sudo lsusb I get:

```
Bus 002 Device 012: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 002 Device 005: ID 046d:c526 Logitech, Inc. 
Bus 002 Device 004: ID 04b8:0005 Seiko Epson Corp. Stylus D88+
Bus 002 Device 002: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 046d:c70a Logitech, Inc. MX5000 Cordless Desktop
Bus 006 Device 003: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth Laser Mouse
Bus 006 Device 002: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

The device is:

```
Bus 002 Device 012: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
```
which is shown above in the *sudo lsusb*. 

I know this because when I turn off the external usb enclosure and do a *sudo lsusb* it does not show up in the output. 

Here is the output of *sudo fdisk -l*:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70667066

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       42443   340923366    7  HPFS/NTFS
/dev/sda2           42444       60801   147460635    f  W95 Ext'd (LBA)
/dev/sda5           42444       47670    41985846    7  HPFS/NTFS
/dev/sda6           47671       50102    19535008+  83  Linux
/dev/sda7           50103       58856    70316473+  83  Linux
/dev/sda8           58857       59342     3903763+  82  Linux swap / Solaris
/dev/sda9           59343       60801    11719386    b  W95 FAT32

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x043f043e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      775218   390709840+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x127589c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c5d0935

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS

```


This drive has worked for me in the past. Don't know why now it does not want to work now. 

Any help is appreciated.

---

### Post by killabee44 on 2009-07-07
After a couple of reboots it worked. Go figure. I still would like to know why this happens. I always eject my devices properly.

One thing I did notice..

While rebooting, the dialog showed something failed. It said something to the effect that it "failed to mount ntfs filesystems" \sbin\mount.ntfs

Sounds like it's related to my problem.

---

### Post by fethio on 2009-11-08
Killabee,
I am experiencing the same problem right now, with the same hardware. fdisk -l see my new drive. However, until now I haven't figured out yet a way to get along with transferring a clone of my existing disk, to the wanne-be. actually thread #599599 seems to be good as a reference to using dd, and the software clonezilla is an alternative. Also March and April columns of Kyle Rankin contain good stuff (in Linux Journal vols 179 and 180)

I'm just curious if you have anything to say about this. Anyhow thanks for the tip::
sudo fdisk -l
that lightened my heavy heart when ubuntu seemed not to detect the external disk and windows did (my wife's computer, I hacked it when she was sleepin)
fethio

---

### Post by tsucol11 on 2009-11-08
I noticed th same thing on one of my MB's. I had just upgraded the Bios to the last version to enable the board to see over 4gigs of memory. Upon rebooting (several times) my external drive was not being noticed during POST, so I could not boot into Ubuntu. USB mouse also froze in ubuntu on the rare occassions it did start.

Problem was solved when I cancelled the automatic (NOS) overclocking on the MB (ASUS), The new BIOS & overclocking was causing USB corruption. Everything is back to normal now.

Brian

> **fethio said:**
> Killabee,
I am experiencing the same problem right now, with the same hardware. fdisk -l see my new drive. However, until now I haven't figured out yet a way to get along with transferring a clone of my existing disk, to the wanne-be. actually thread #599599 seems to be good as a reference to using dd, and the software clonezilla is an alternative. Also March and April columns of Kyle Rankin contain good stuff (in Linux Journal vols 179 and 180)

I'm just curious if you have anything to say about this. Anyhow thanks for the tip::
sudo fdisk -l
that lightened my heavy heart when ubuntu seemed not to detect the external disk and windows did (my wife's computer, I hacked it when she was sleepin)
fethio

---

### Post by killabee44 on 2009-11-08
Guys,

I am still a newbie to linux but learning every day. I never had this problem again. For some reason it just never happened again. Wish Icould help. :(

---

