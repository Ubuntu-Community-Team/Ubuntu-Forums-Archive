---
title: "rsync bootable disk backup  /dev/sda to /dev/sdb"
date: 2011-09-14
forum: General Help
---

### Post by deniro on 2011-09-14
Ubuntu Gurus
I use ubuntu 10.04 64-bit
 
I have disk /dev/sda partitioned as /dev/sda1(/) and /dev/sda2(swap)
I want to full backup everything to /dev/sdb and make /dev/sdb bootable as well.
After the full backup I want to continue incremental backups to /dev/sdb with rsync etc...
 
1--  should I partition my /dev/sdb as /dev/sda?  or no /dev/sdb partitioning needed.
 
2-- after full, I wanna perform manual incremental backup  with tools like rsync..
      so, I think full backup must be compatible with rsync
  how can I achieve that full backup from /dev/sda to /dev/sdb...
 
3-- backup /dev/sdb must be bootable in case  /dev/sda crashes.
I think for that I need to create grub on /dev/sdb with live cd and  change /etc/fstab
what else might be necessary to change/update  for /dev/sdb boot
 
 
I would like to hear  all good solutions/links/document to backup my /dev/sda to /dev/sdb and  continue to manually perform incremental backups with rsync or similar.. (dont want full backup everytime.. just sync changes after full backup)
 
Note: I dont wann use clonezilla or similar disk image tools. After full disk backup I wanna continue incremental backups manually in a controlled manner like at certain points or times.
 
I consider rsync as my best shot at this time but I am not quiete sure how to make /dev/sdb as my bootable  copy of /dev/sda with rsync
 
In addition, I curious to explore rsnapshot if you can point to any good docs/links etc...
 
All suggestions are welcomme..
 
thx
deniro--

---

### Post by dcstar on 2011-09-15
> **deniro said:**
> Ubuntu Gurus
I use ubuntu 10.04 64-bit
 
I have disk /dev/sda partitioned as /dev/sda1(/) and /dev/sda2(swap)
I want to full backup everything to /dev/sdb and make /dev/sdb bootable as well.
.........
In addition, I curious to explore rsnapshot if you can point to any good docs/links etc...
 
All suggestions are welcomme..
 
thx
deniro--

Or you could consider using RAID-1 partition mirroring using the mdadm system.

---

### Post by deniro on 2011-09-15
NO, I am not looking mirroring solution.. I am looking  backup solution and 
syncing at certain times or points manually in controlled way..
thx

---

