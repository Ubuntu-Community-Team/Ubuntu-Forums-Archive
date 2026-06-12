---
title: "Transferring/Recovering RAID0 - NTFS, No superblock?"
date: 2011-06-14
forum: General Help
---

### Post by mohsan on 2011-06-14
My motherboard failed, and now I am trying to recover my data from the RAID0 configuration that I had that consisted of 2 500GB SATA hard drives.  It was configured using the on-board RAID controller (AMD, SB700) on a Gigabyte MB.  I was running Windows 7, and the RAID0 array was formatted as 3 NTFS partitions (OS, Apps, Data).

I took the 2 HDs and installed them in a different computer (with RAID disabled), and booted Ubuntu-Live.  From some discussions, I read I was hoping that Ubuntu would automatically recognize the RAID, however I didn't have this luck.  The two hard drives show up in the Disk Utility application as Healthy and I've attached the screen shots for further analysis.

Also, I tried to manually use mdadm to detect the array, but no luck there.  Here's the log from that:

ubuntu@ubuntu:/$ sudo mdadm --assemble --scan
mdadm: No arrays found in config file or automatically
ubuntu@ubuntu:/$ sudo mdadm --examine /dev/sda
mdadm: No md superblock detected on /dev/sda.
ubuntu@ubuntu:/$ sudo mdadm --examine /dev/sda1
mdadm: No md superblock detected on /dev/sda1.
ubuntu@ubuntu:/$ sudo mdadm --examine /dev/sdb
mdadm: No md superblock detected on /dev/sdb.
ubuntu@ubuntu:/$ sudo mdadm --examine /dev/sdb1
mdadm: cannot open /dev/sdb1: No such file or directory
ubuntu@ubuntu:/$ 

Right now, I'm out of ideas of what to try next.  I would appreciate it any help with this, as I'm really desperate to recover the data on this drive.

---

