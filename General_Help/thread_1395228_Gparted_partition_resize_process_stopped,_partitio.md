---
title: "Gparted partition resize process stopped, partition lost"
date: 2010-01-31
forum: General Help
---

### Post by enigmatichus on 2010-01-31
Hello. I have an enormous problem. I was resizing my ubuntu partition from 30 Gb to 60 Gb using an unallocated space obtained deleting an unused windows partition. Everething was going well, gparted was copying data from the old partition to the new space, but by little brother accidentally closed the lid of my laptop. Of course I was using a live image for the work on my hard disk, so the system went in standby. When I reopened the lid, the system was frozen. After waiting a lot, I restarted the pc, and grub was destroyed. So I rebooted with the live cd, and reopening gparted I see that now my old partition give an error, and the program tell me that it has got an unknown or damaged filesystem. Now I don't know what to do, there is a lot of essential data in my disk, please, help me. I feel lost, I can't loose all my data. Thank you.

---

### Post by J V on 2010-01-31
> **enigmatichus said:**
> Now I don't know what to do...If I were you I would start by killing my little brother :)

There are a few disc recovery options, just make sure you DONT write to the disc/partition until you use it...

Testdisc comes highly praised by many, try it.

---

### Post by enigmatichus on 2010-01-31
> **J V said:**
> If I were you I would start by killing my little brother :)

There are a few disc recovery options, just make sure you DONT write to the disc/partition until you use it...

Testdisc comes highly praised by many, try it.

Oh, God!! It worked!! I run testdisk under the livecd and the program was able to find my root partition, so I wrote a new partition table and then, after a reboot I mounted it and I reinstalled grub! Now everything works, I'm making a huge backup of all my files, and then I will complete the process I started and failed to complete. Thank you very much, you saved me!! I can't tell you how much I am happy now!! Thank you again!! Problem solved!! :)

---

### Post by J V on 2010-02-01
Killed your little brother? :D

---

