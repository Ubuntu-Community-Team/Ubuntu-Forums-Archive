---
title: "What does this log file mean? Thanks!"
date: 2011-04-12
forum: General Help
---

### Post by listerdl on 2011-04-12
I guess my question has two parts about being able to read and understand the log file viewer.

My system, (10.04 LTS running on a Solid State Drive) froze and I checked out the log that offered this explanation:

```
 Apr 10 22:20:34 ubuntu gdm-session-worker[1193]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN
``` 

Any ideas what this is? My hunch is that there is a connection between the SSD and the system freezing in ubuntu. The reason why I think that is because my log file viewer is littered with this instance:

```
Apr  9 18:28:24 ubuntu kernel: [ 4213.956244] ata4: EH complete
Apr  9 18:28:25 ubuntu kernel: [ 4214.583748] ata4: limiting SATA link speed to 1.5 Gbps
``` 

It seems by this above log that there is an issue with the SATA drive. What is weird though is that when I tested the drive in windows, (I dual boot) the SMART reading was 99% healthy.

It seems that 10.04 has a problem with my Crucial 120 Gig SSD?

Any ideas! Thanks!

Also, is worth noting that my machine has only frozen twice in hundreds of cycles.

---

### Post by rubylaser on 2011-04-12
Have you tried a different cable, or SATA head on the motherboard.  Your SSD should be running at SATAII speeds. I'd also be looking at SMART errors to check for a bad cable, or problems with the drive.  UltraDMA CRC Error Count is one that can indicate a poor connection.

---

### Post by listerdl on 2011-04-12
> **rubylaser said:**
> Have you tried a different cable, or SATA head on the motherboard.   I guess that is relatively easily done. Only problem is that I would have to completely take apart the laptop to get to the motherboard connection.

> **rubylaser said:**
> Your SSD should be running at SATAII speeds. I'd also be looking at SMART errors to check for a bad cable, or problems with the drive.   How can I check for SMART errors in linux? Also, it is worth noting that in windows the SMART reads 99% healthy - so that is odd and makes me think that the 10.04 kernel does not like my SSD? Is that possible?

> **rubylaser said:**
> UltraDMA CRC Error Count is one that can indicate a poor connection. Not sure how to check for this - I searched online but no joy.

Thanks for your help

---

