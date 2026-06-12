---
title: "Question about ubuntu software RAID"
date: 2010-10-19
forum: General Help
---

### Post by peap on 2010-10-19
Consider the following setup:

Ubuntu system installed on a separate SSD for speed.
An ubuntu software RAID array consisting of X number of physical HDD's for storage (RAID6 or RAID10). RAID setup is done during system install.

If I suffer a total crash of the SSD and loose my system, will I be able to, using a new system disk, "reconnect" to the RAID array even if the "mothersystem" of the software RAID is lost?

If yes, are there any particular config- or system files I need to backup to be able to rescue the array or will it just be recognized "out-of-the-box" when reinstalling ubuntu?

---

### Post by amauk on 2010-10-19
> **peap said:**
> If I suffer a total crash of the SSD and loose my system, will I be able to, using a new system disk, "reconnect" to the RAID array even if the "mothersystem" of the software RAID is lost?Yes
You can move the array to any other (linux) machine

> **peap said:**
> If yes, are there any particular config- or system files I need to backup to be able to rescue the array or will it just be recognized "out-of-the-box" when reinstalling ubuntu?(assuming you're using mdadm to manage the RAID)

Just backup this file```
/etc/mdadm/mdadm.conf
```

Then you can pop the disks into any other machine, install mdadm, copy over the config file, reboot the machine, mount the array, and off you go

---

### Post by peap on 2010-10-19
Thanks, sounds pretty much like I imagined it. Just want to be sure before I go ahead and buy my hardware.

Is it my motherboard that decides if I will be able to hotswap hdd's in my array? I'm not sure about the terminology but by hotswap I mean changing a hdd without shutting down the computer.

---

### Post by psusi on 2010-10-19
> **peap said:**
> Thanks, sounds pretty much like I imagined it. Just want to be sure before I go ahead and buy my hardware.

Is it my motherboard that decides if I will be able to hotswap hdd's in my array? I'm not sure about the terminology but by hotswap I mean changing a hdd without shutting down the computer.

Yes, you have to have a controller and socket in the chasis built for hot swap, which typically only happens in rack mount servers.

Also you don't HAVE to back up mdadm.conf.  You can recreate it if you need to with the proper mdadm command, though backing it up does save you that step.

---

### Post by peap on 2010-10-19
Thanks guys.

---

