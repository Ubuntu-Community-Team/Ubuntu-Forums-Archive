---
title: "(possibly) bogus warning by SMART?"
date: 2010-12-22
forum: General Help
---

### Post by obzabor on 2010-12-22
I get warnings by Disk Utility about "imminent hard disk failure", which is very scary indeed. When I go into the details, I see very high "reallocation count" of 3,245 sectors. I searched on the forums, and everyone urges people to backup their data and buy a new hard drive in this situation.

Problem is, my other hard drive shows EXACTLY the same value of 3,245 sectors. Yesterday these values were 3,222 and 3,223. I'm wondering how two hard-drives could have failed in exactly the same manner, at exactly the same time.

Both hard-drives are SATA drives, in a dual-disk external USB enclosure. Used for about a year with no issues. I upgraded to Ubuntu 10.04 LTS when it came out, was on 9.04 before.

I installed smartmontools and ran smartctl --all /dev/sdb. It said "Device does not support SMART". Same command worked OK on /dev/sda (my main hard drive).

Please help - how can I make sure this is a disk issue, and not SMART or USB enclosure issue?

---

