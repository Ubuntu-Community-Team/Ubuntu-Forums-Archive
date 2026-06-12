---
title: "CFDisk Problems"
date: 2006-05-09
forum: General Help
---

### Post by gotvols on 2006-05-09
When I try to use cfdisk it gives me the following error:

opened disk read-only - you have no permissions to write

How do I fix this problem? Any help would be appreciated.

I don't have this problem with operating systems like: Fedora, PC-Bsd, and Ubuntu.
I do have this problem when I tried to install Gentoo, Easys, and FreeBSD.

I have a serial ata hard drive which I just got in the past week. I use to use a ide hard drive and I didn't have this problem. I don't know if that's the problem or not.

---

### Post by garner_nc on 2006-05-09
I would expect that your trying to use CFdisk on a mounted drive. You probably need to boot from a live CD and run CFdisk or Gparted from there.

All the best,
Doug Whtie

---

### Post by gotvols on 2006-05-11
I tried ubuntu live cd and it still no luck.

---

### Post by jtibau on 2006-05-11
I've used cfdisk with a disk with mounted partitions... Although I've just used it for looking at the partition table.
Did you run cfdisk as root?
sudo cfdisk /dev/hda
If you haven't then that's the problem. Other distros usually allow you to login as root out of the box. But in ubuntu you have to do everything with sudo.

---

