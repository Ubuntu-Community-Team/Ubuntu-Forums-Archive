---
title: "mount: only root can mount"
date: 2010-04-23
forum: General Help
---

### Post by wefallaround on 2010-04-23
I'm having an issue with my mounted 'media' partition on Ubuntu 9.10. Since rebooting an hour ago the drive is showing as busy (activity light) but I cannot access it. When I try to open the mount I get the message:

mount: only root can mount /dev/sda6 on /media/mediadrive

I have tried unmounting the drive but I get the message:

mount: /dev/sda6 already mounted or /media/mediadrive busy

when I run sudo fuser -m /dev/sda6 I can see that the fsck.ext3 process is running on the drive (by matching the pid)

I'm not sure what to do. Is fsck preventing my drive from mounting? Am I just being impatient here.

I would really appreciate some advice. I have about 1TB of media on that mount!

---

### Post by gzarkadas on 2010-04-23
A filesystem check is run on your drive; patience, when it is finished you will be able to use it :).

---

### Post by wefallaround on 2010-04-26
Panic over. You were quite right. I left it overnight and when I rebooted in the morning everything was back to normal. It has forced me to back up more wisely in future, just in case anything 'real' happens

---

