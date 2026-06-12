---
title: "u3-tool - Device reported command failed"
date: 2010-05-09
forum: General Help
---

### Post by conmat on 2010-05-09
I'm trying to use u3-tool to remove the u3 stuff from a SanDisk 2 GB Cruzer usb drive.

Every command I issue returns:
u3_partition_info() failed: Device reported command failed: status 1

fdisk -l and lshw give the drive name as /dev/sdb.

the gui disk utility gives the drive name as /dev/sr1.

I have tried both names.

I can get this:
foobar@foobar:~$ sudo u3-tool -D /dev/sdb
u3_partition_info() failed: Device reported command failed: status 1
u3_data_partition_info() failed: Device reported command failed: status 1
Chip info:
 - Manufacturer: SanDisk 
 - Revision: 3.21

Property page 0x03:
 - Device size: 2055021056 byte(0x003d3e91)
 - Device serial: 000017501B6033FD
 - Full record length: 0x00000077
 - Unknown1: 0x03
 - Unknown2: 0x54060781
 - Unknown3: 0x54060781

Property page 0x0C:
 - Max. pass. try: 100

A google search gives this:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2075851.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2075851.html)

Any info appreciated.  THX

---

### Post by Sianegad on 2010-11-03
Hi i am trying to find info on the same matter did you have any luck since posting this?

---

### Post by conmat on 2010-12-06
Hi,

I never received any suggestions and I gave up.  I still have the drive and I'll try again when I have time.

---

