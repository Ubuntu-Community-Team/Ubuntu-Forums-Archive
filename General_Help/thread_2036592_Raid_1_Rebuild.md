---
title: "Raid 1 Rebuild"
date: 2012-08-02
forum: General Help
---

### Post by Mick Bentley on 2012-08-02
I'm running 10.04 LTS Desktop 64bit, with two identical disks set up as a raid 1 array. Last week I kicked the power lead from the back of the PC  Using the rescue disk to repair grub, I can now boot from  sda2 mounted at /, while sdb2 seems OK  but not mounted. 

The swap partitions, sda1 & sdb1, still appear to be part of raid mdb1.

Can someone kindly please advise me how to reassemble the boot/data part of the raid, using sda2 as the master disk and overwriting sdb2?

Everything on sda2 has been backed up.  Mdadm & mdstat output is attached.

Mick

---

### Post by Mick Bentley on 2012-08-14
Bump. Or should I now be using AskUbuntu?

---

