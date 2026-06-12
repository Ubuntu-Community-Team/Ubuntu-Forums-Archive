---
title: "RAID advice"
date: 2010-09-20
forum: General Help
---

### Post by looter211 on 2010-09-20
Currently I have a 500gb drive with Ubuntu on half of it.  The other half is a soon to be Win7 install.  I just picked up an identical drive for real cheap last week and I am interested in advice for going about setting up a RAID 1 for redundancy.  

My first road block is do I want software or hardware RAID?  Is this even possible with a dualboot system?  

If hardware RAID is the way to go does anyone have a particular brand or model they could recommend?  

Thanks ahead of time.

---

### Post by looter211 on 2010-10-11
*bump*

42 views and not one suggestion?

---

### Post by kumaryu on 2010-10-12
As a general rule, if you intend to have a dual boot system, you would need the RAID function provided on either the motherboard or from a separate hardware RAID controller. (An alternative maybe to have only specific OS partitions in the RAID set but this adds to complexity.)

If your intention is redundancy as opposed to performance, hardware RAID options would make better sense since the integrity of data on the disks and the ease of recovery are not dependent on OS or software elements.

Since many H/W RAID implementations depend on proprietary disk formats it would be best to set it up before any operating systems are installed.

One further observation that I would make is that RAID adds an additional level of complexity to the system. This means that there are more things that can go wrong and more things to account for when things do go wrong. (eg. On a hardware RAID, if the RAID controller fails, you would need to have to have another controller to restore the functionality.)

Its important to plan out your data backup and recovery plans before attempting any of the options. It also important to remember that RAID is not a replacement for backup.

---

