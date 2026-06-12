---
title: "question about XFS and raid.."
date: 2010-03-17
forum: General Help
---

### Post by stek_87 on 2010-03-17
I get "Disabling barriers, trial barrier write failed" in my syslog.

IS this because "barrier" is not supported for an /dev/mdX device?
(filesystem is XFS on a 4TB raid5 volume (3*2TB sata))

/S

---

### Post by stek_87 on 2010-03-17
> **stek_87 said:**
> I get "Disabling barriers, trial barrier write failed" in my syslog.

IS this because "barrier" is not supported for an /dev/mdX device?
(filesystem is XFS on a 4TB raid5 volume (3*2TB sata))

/S

Now I have studied some on this on my own and it seems quite important to have this feature enabled. The problem is that it cannot be enabled on an mdadm "mdX" device.

So.. Does anyone know about a smart workaround for this issue??

My server is connected to a UPS, but I really don't want the filesystem to be corrupted if the PSU (for some reason..) goes down.

/S

---

### Post by stek_87 on 2010-03-18
any one..?

---

### Post by resistanceISuseless on 2011-07-30
I myself am looking for XFS on RAID 5.  I'm wondering if it's a good idea or not.  

-resistanceISuseless

---

### Post by stek_87 on 2011-07-31
> **resistanceISuseless said:**
> I myself am looking for XFS on RAID 5.  I'm wondering if it's a good idea or not.  

-resistanceISuseless

I would just go for ext4.

---

