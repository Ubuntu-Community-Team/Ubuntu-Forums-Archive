---
title: "What do I do with /boot when doing software RAID?"
date: 2009-09-17
forum: General Help
---

### Post by Vunutus on 2009-09-17
I'm trying to set up a three disk RAID 5 software array.

I installed everything one time, but when I tried to boot into is I got grub error 17. After googling around I've come to the conclusion that grub cannot read from RAID 5 arrays.

How can I set this up, then? If I just put /boot on one disk, what if that's the one that fails?

Overall I'm a bit confused. Could someone please tell me the ideal partition setup for a three disk software RAID 5 array? I don't want to separate out any partitions that I don't absolutely have to.

What I did this time was 2GB swap with the rest of drive set to bootable RAID volume on all three drives, then configured raid and set my root partition to take the entire raid device.

The two main issues I see with this are:
1. I have no idea what I'm doing with the swap space. I want 2GB total, but again, what if the drive I set it on is the one that fails? Would it be possible to put swap as part of the md device?
2. As mentioned before, what do I do with /boot?

---

### Post by Vunutus on 2009-09-17
Bump. Would really like to get this going by sometime tomorrow...

---

### Post by Vunutus on 2009-09-18
Bump.

---

### Post by Vunutus on 2009-09-18
Ok so what I ended up doing was making two separate RAID volumes. One large RAID 5 array for my root partition (and therefor main data), and a small 500MB RAID 1 array on each drive. Since /boot is being mirrored automatically on each drive, I assume this will leave me with a bootable system no matter which drive fails?

Also, is there any technological reason why grub won't read from RAID 5 arrays, or is it just not yet implemented in grub?

---

### Post by Slim Odds on 2009-09-18
> **Vunutus said:**
> Also, is there any technological reason why grub won't read from RAID 5 arrays, or is it just not yet implemented in grub?

Because the RAID drivers are not loaded yet.

I have a separate boot partition on my RAID 0 setup. That's just the way it is.

---

