---
title: "mke2fs, tune2fs and mount options for performance / RAID1 for swap?"
date: 2010-04-23
forum: General Help
---

### Post by apeganz on 2010-04-23
edit: there seems to be a problem with my browser, all my newlines disappeared. I'm putting my text in code-tags (hope they exist here and will fix that). edit2: nope, made it worse. removing them again, sorry for the wall of text :(  any ideas what's going wrong?   Hello everyone (first post, woo)!  I'm in the process of installing Ubuntu Server x64 for the first time and I'm at the formating stage. After working through the man pages and googling I still couldn't determine what some of the options for mke2fs and tune2fs do for performance or data safety.  I hope you can help me out:  The system has 2 40GB disks for the OS and 3 2TB disks for storage. The 40GB disks have 6 (7 in fact if you count the extended partition) partitions each, working as 6 mdadm RAID1 devices. The 2TB drives just have one huge partition each, working as a 4TB mdadm RAID5. The 6 RAID1-devices will be used for /boot (ext2), /swap, /, /etc, /root and /home (all ext4, the RAID5 device will be ext4 too).  Here the first question arises: does it make sense to have a /swap in RAID1? My thinking is somewhat like this: If a process has to use swap and the disk w/ the swapped data fails, that process will crash, hence RAID1 would be good, and as soon as there is swapping it's slow anyway. But I have no idea how big of an performance impact that would actually have. So: good idea or not?  With mke2fs I can't figure out what impact -f has and what the best values would be; and if I should use -j when I use -J to set the journal size to 256 MB. Any suggestions?  With tune2fs -o I can set journal_data and journal_data_ordered. I'd prefer to use both for data safety reasons, but again I don't know how much performance that would cost. What would you do?  And finally the mount options: What's the difference (again performance- and safety-wise) between async and sync, dev and nodev, suid and nosuid? There was one more thing with mounting, but I'm afraid I forgot.   I appreciate your help, Alex

---

