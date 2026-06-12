---
title: "528 format"
date: 2010-06-08
forum: General Help
---

### Post by aza zar on 2010-06-08
Hello 

I have a SAS drive 512 byte, and want to format it to 528 byte
tried the following commands but it did not work

sg_format --format --size=528 /dev/sdb

but when I checked with 

sdparm --command=ready /dev/sdb

I see that the drive is not ready.....  also tried to change the sense mode also -l -p 

sg_modes --six /dev/sdb
sg_format --format -l -p --size=528 /dev/sdb

Please help! I am a total newbie :confused:

---

