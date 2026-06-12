---
title: "Is there a command to re-scan HDD size?"
date: 2011-12-01
forum: General Help
---

### Post by Roasted on 2011-12-01
Today I randomly got a message saying I had 0% space left on my home directory. My home directory is a pair of 1 TB drives in mdadm raid 1 mirror. I only had about 400 GB on my home directory, so I knew something was off.

I rebooted, and sure enough it was fixed.

I'm wondering if there was a command to re-scan the system to acknowledge what the true usage is without rebooting. I can only imagine that if I had waited long enough it would have done it on its own??

---

### Post by wolfen69 on 2011-12-01
I use 
```
sudo fdisk -l
```

---

### Post by Roasted on 2011-12-01
> **wolfen69 said:**
> I use 
```
sudo fdisk -l
```

That just shows the partitions on the disks... does that somehow re-trigger the system to look at what space is used/free to cause Conky, System Monitor, etc. yield the proper numbers then?

---

