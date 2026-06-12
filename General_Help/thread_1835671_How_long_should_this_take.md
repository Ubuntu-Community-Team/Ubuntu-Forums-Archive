---
title: "How long should this take?"
date: 2011-08-29
forum: General Help
---

### Post by lsutiger on 2011-08-29
I have to clean a hard drive of data. I am running :
dd if=/dev/urandom of=/dev/sdc

It has been running for over 24 hours! There is activity on the drive from the hard drive light. The drive is fairly new, 7800 rpm, but 500GB. I know it is fairly large, but does it ever end or do I have to kill it?

---

### Post by plucky on 2011-08-30
> **lsutiger said:**
> I have to clean a hard drive of data. I am running :
dd if=/dev/urandom of=/dev/sdc

It has been running for over 24 hours! There is activity on the drive from the hard drive light. The drive is fairly new, 7800 rpm, but 500GB. I know it is fairly large, but does it ever end or do I have to kill it?

You have to kill it,as all it is doing is writing random data to the drive.

Good luck

---

### Post by mcduck on 2011-08-30
With that command, until the end of the world. ;)

You didn't specify how much data should be written, so dd will continue as long as there is data available from /dev/urandom. Just kill the command with Ctrl-c.

---

### Post by lsutiger on 2011-08-30
I found you can track the progress of this command: sudo kill -USR1 $pid ($pid found from doing an ps)...It has been about 1 1/2 days an it is not done. Please do research before you spout your 'knowledge'.
This command will take quite some time, but it will end in time.

---

