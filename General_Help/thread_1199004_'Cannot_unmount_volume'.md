---
title: "'Cannot unmount volume'"
date: 2009-06-28
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2009-06-28
How do I get my dvd player to eject a dvd when avidemux crashes and I get this error message. I always end up rebooting to get it out of the drive. Is avidemux still running and I just can't see it even though it crashed?

---

### Post by swisstone198 on 2009-06-28
try 

sudo umount /dev/dvd


ADDED

if that doesn't work you can use fuser to kill any process using the drive

sudo fuser -km /dev/dvd

then try umount again

---

### Post by ihatetryingtopickaloginna on 2009-06-28
It replies that the device is busy when I send the command.

---

### Post by ihatetryingtopickaloginna on 2009-06-28
The second one worked. Thanks.

---

