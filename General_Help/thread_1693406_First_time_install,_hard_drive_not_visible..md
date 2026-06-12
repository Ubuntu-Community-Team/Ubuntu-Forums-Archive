---
title: "First time install, hard drive not visible."
date: 2011-02-22
forum: General Help
---

### Post by k.hommy on 2011-02-22
I used unetbootin to put ubuntu 10.10 on a 2 gb usb key. I started up using the "try before installing" option and when I try to install in full it says I do not have 2.5 free gb's for the install. So I open up gparted only to find that only drive there is my 2bg usb key and I have no idea how to find my main hard drive. 

I tried searching and tried the following; 
I checked the sata setting in the boot menu and it is IDE. The computer has also never been used in a raid setup. 

Any ideas? Thanks

---

### Post by k.hommy on 2011-02-23
Bump, anyone?

---

### Post by seawolf167 on 2011-02-23
When you click the "try Ubuntu first" and get to the desktop, open up a terminal

Applications -> Accessories -> Terminal

and type the following command in to list all your partitions (mounted or not) so we can see what you are working with

```
sudo fdisk -l
```

and paste in a reply

or type 

```
sudo fdisk -l > ~/Desktop/fdisk-output.txt
```

then you can email yourself the text on the desktop (called "fdisk-output.txt") file to paste here

---

### Post by k.hommy on 2011-02-23
```
Disk /dev/sda: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders
Units = cylinders of 342 * 512 = 175104 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          24       11534     1968128    b  W95 FAT32

```

It's only seeing my usb stick, and I have no idea why

---

### Post by seawolf167 on 2011-02-24
Lets go back to the beginning, please check the following:


[LIST]
[*]that the drive is receiving power (i.e. plugged into a power molex)
[*]that the drive is connected to your motherboard via SATA or IDE cable
[*]that you have the drive port enabled in BIOS (F2, DEL, ESC, F10 - one of these keys will allow you to enter BIOS when booting)
[*]that you have the correct mode enabled for the drive (i.e. SATA/PATA combination, etc.)
[/LIST]
If there is no problems with the above but the drive still isn't working, the next thing would be to run the S.M.A.R.T test and plug the drive into another computer and check to see if the drive is actually working.

---

### Post by k.hommy on 2011-02-24
Drive is powered, connected and enabled, and set to sata and IDE in the bios settings. I am working on a netbook, if that changes anyting (acer spire one).

One time ubuntu managed to find the hard drive, during the install and it said it was 250gb so I said format it all and install the OS. Then it hit me, my hard drive is only 160gb so when ubuntu did this format, did it essentially corrupt my drive or something along those lines?

---

### Post by seawolf167 on 2011-02-24
Fdisk should still be able to see the hard drive and any partitioning

if you type in

```
sudo lshw -class disk
```

you should be able to see your disk listed

If it isn't listed still, make sure you run the S.M.A.R.T. tests since I suspect a failed drive. If your drive is a WD drive, you can use their [bootable cd ]("http://support.wdc.com/product/download.asp?groupid=614&sid=30&lang=en")to check the drive status

---

