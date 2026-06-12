---
title: "Testdisk results - HELP"
date: 2011-06-18
forum: General Help
---

### Post by August59 on 2011-06-18
Laptop running Windows 7 with Primary partition and 2 logical partitions on a Hitachi 500GB 7200 rpm 2.5" hard drive.
 
Started having boot problems and then not able to boot. Then partitions stated disappering and now Testdisk cannot find a partition at all. It ran for 28 hours and came up with nothing.
 
I forgot what screen I got back to, but it had these results and I have no idea what it means:
 
Disk: /dev/sda-500gb / 465 GIB - CHS 60801 255 63
 
Checking current partition structure
[151252.113785] sd 0:0:0:0:0 [sda] unhandled error code
[1512Partition] sd 0:0:0:0:0 [sdaStartult:hoseEnd size in sectorsriverbyte=DRIVER_OK
[151252.114219] sd 0:0:0:0:0 [sda] CDB: read(10):28 00 00 00 00 00 00 00 08 00
[151252.114475] end_request: I/O Error, dev sata, sector 0
Partition: Read errorr(it actually spelled error this way), I/O Error on device sda logical block 0
Current partition structure:
 
 
Was going to run "PhotoRec", but it is not on the GParted disk that I'm using. At least I don't think it is????
 
Any help would be greatly appreciated
 
PS - At the moment it is running in the "Deeper Search" mode.

---

### Post by prodigy_ on 2011-06-18
"I/O error" suggests a possible hardware problem.

---

### Post by wildmanne39 on 2011-06-18
> **August59 said:**
> Laptop running Windows 7 with Primary partition and 2 logical partitions on a Hitachi 500GB 7200 rpm 2.5" hard drive.
 
Started having boot problems and then not able to boot. Then partitions stated disappering and now Testdisk cannot find a partition at all. It ran for 28 hours and came up with nothing.
 
I forgot what screen I got back to, but it had these results and I have no idea what it means:
 
Disk: /dev/sda-500gb / 465 GIB - CHS 60801 255 63
 
Checking current partition structure
[151252.113785] sd 0:0:0:0:0 [sda] unhandled error code
[1512Partition] sd 0:0:0:0:0 [sdaStartult:hoseEnd size in sectorsriverbyte=DRIVER_OK
[151252.114219] sd 0:0:0:0:0 [sda] CDB: read(10):28 00 00 00 00 00 00 00 08 00
[151252.114475] end_request: I/O Error, dev sata, sector 0
Partition: Read errorr(it actually spelled error this way), I/O Error on device sda logical block 0
Current partition structure:
 
 
Was going to run "PhotoRec", but it is not on the GParted disk that I'm using. At least I don't think it is????
 
Any help would be greatly appreciated
 
PS - At the moment it is running in the "Deeper Search" mode.Hi, is sounds like you need to get your files backed up on an external drive fast, I am going to give you a guide on how to get your files with the livecd. 
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by August59 on 2011-06-20
Thanks guys, I really appreciate your help. I had Photorec up one time and it sa w my partitions, but i could not figure out how to get photorec to recover files to my usb hard drive which it recognized when it booted up?
 
It doesn't look like it shows up in my list so that I can pick it.
 
Sorry, if I sound so noob! I do like the software "testdisk" as it has saved mine and some of my friends butts a few times!

---

