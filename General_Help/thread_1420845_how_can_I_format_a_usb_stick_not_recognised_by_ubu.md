---
title: "how can I format a usb stick not recognised by ubuntu"
date: 2010-03-03
forum: General Help
---

### Post by lavy on 2010-03-03
Hi,

I inserted a USB stick in the drive. Ubuntu didn't recognized it automatically. I tried using the lsusb command.

With the device unplugged I received the following output:
$sudo lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 006 Device 003: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 006 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c050 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

with the device plugged in I received the following output:
Bus 008 Device 007: ID 090c:3000 Feiya Technology Corp.
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 006 Device 003: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 006 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c050 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I assumed my USB is device 007 so I've tried the command:
$ sudo lsusb -D 007
Cannot open 007

Then I decided to format the drive, so I tried to identify the device using fdisk. I typed:
$ sudo fdisk -l

Problem is that fdisk command only shows my hard disks and not the usb drive.

How can I format the usb drive?

I'm using Ubuntu 8.04, KDE 3.5

Tx

---

### Post by indiana_crook on 2010-03-03
If you have access to a windows computer and format it, it should work with ubuntu.  That worked for me anyways.

---

### Post by lavy on 2010-03-04
I tried that, but problem is it doesn't work on windows either :mad:

---

### Post by kanikilu on 2010-03-04
If it's not showing in fdisk or on Windows (you checked Disk Management and not just Windows Explorer, right?), maybe you have a dead stick?

...I had an 8gb drive do the same thing to me last week :(

---

### Post by lavy on 2010-03-06
Hi,

I did, he device manager sees it but when I try to format it windows does nothing :confused:

---

