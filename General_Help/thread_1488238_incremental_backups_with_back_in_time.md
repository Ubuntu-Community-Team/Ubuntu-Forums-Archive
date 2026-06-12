---
title: "incremental backups with back in time??"
date: 2010-05-19
forum: General Help
---

### Post by Andrew Golightly on 2010-05-19
Hi there,

I did a backup with back in time yesterday. And that came to 30gb. then I added a small 25kb file to my documents, and to see what happens, re-did a backup using back in time. I see it has re-backed up everything again... so 30+gb again.

I just thought it backed up the differences from the last backup??

Backups are going to fill up my external harddisk very quickly if each backup is a complete backup of all folders if ANY change is made.

Does this sound like normal behaviour for back in time?

thanks,
Andrew

---

### Post by -humanaut- on 2010-05-19
I haven't used "back in time" but since real time backups aren't supported yet in Linux filesystems I'd assume thats quite normal I'd recommend more conviental backups such as CD-R's & Usb pendrives or even separate partitions I have a 5 GB fat32 partition that I leave unmounted to backup important files too. Ceph & Btrfs will make real-time backups a reality next release. (hopefully Btrfs will atleast be supported I don't know about Ceph but I hope it's supported It was just recently added to the Linux Kernel.)

---

