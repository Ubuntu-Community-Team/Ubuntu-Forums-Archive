---
title: "df utility and Disk Utility"
date: 2010-11-16
forum: General Help
---

### Post by 55tptag on 2010-11-16
Hi,

I don't understand disk sizes in Linux. Can someone help me out?

I have a 500GB drive. It's ext4. I have run "tune2fs -m 0" on it to reserve the amount of space reserved for root to 0.

I'm using Ubuntu 10.04 that comes with a Disk Utility. When I run "System->Administration->Disk Utility (palimpsest)" the disk shows up as 500GB (see picture). But when I run df -h it shows up as 459GB. So, I don't understand the discrepancy.

When I run df I get the following:
$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sdb1 459G 448G 12G 98% /home

Question: Why is Disk Utility showing me something different than "df"?

==========================
Solution:
I re-read the man page and now ran df with the H option and get:
$ df -H
Filesystem Size Used Avail Use% Mounted on
/dev/sdb1 493G 481G 12G 98% /home

---

