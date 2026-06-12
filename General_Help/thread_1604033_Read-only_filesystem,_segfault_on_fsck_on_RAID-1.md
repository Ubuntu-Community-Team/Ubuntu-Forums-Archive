---
title: "Read-only filesystem, segfault on fsck on RAID-1"
date: 2010-10-23
forum: General Help
---

### Post by lycofron on 2010-10-23
Hi everybody,

this is a hard one (to me, at least).

I have a box running Karmic Koala. Its main job is to backup a web server, so, it runs rsnapshot on a daily basis. Plus, it serves as storage. So, it has two 750GB disks mirroring (RAID-1), on ext3.

Last Sunday, my box was not responding. Logging in by ssh, I received the message "read only filesystem" so, I rebooted. I found out that fsck was not able to correct the filesystem by itself, so, I downloaded a Knoppix CD (mdadm is not installed on Ubuntu Live CD), found the raid device and ran fsck on the raid device. Some errors were found, I fixed them all, and then I was able to boot again.

Next day, I found out that rsnapshot did not complete and filesystem was again read-only. Same routine again, Knoppix boot, fsck, then, fsck exited with status 11 (segmentation fault).

By googling here and there, I found out that in such cases, the usual suspect is the RAM. So, I ran memtest86, it found no problems with the RAM (after 6 or so passes).

I wanted to check to see if there is any hardware problem, so, I downloaded Ultimate Boot CD and right now I am running a few tests on the CPU. Right now, there's a stresstest V2.0 going on, but no errors so far.

I still suspect a hardware problem, however, I was not able to find the culprit so far. I mean, rsnapshot takes about an hour or less. Tests on RAM and on CPU running for two hours would have revealed the problems - or would they?

This is as far as I can get right now. Any ideas?

Thank you in advance.

---

