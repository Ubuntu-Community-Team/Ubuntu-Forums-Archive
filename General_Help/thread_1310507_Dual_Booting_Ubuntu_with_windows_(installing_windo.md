---
title: "Dual Booting Ubuntu with windows (installing windows after ubuntu)"
date: 2009-11-01
forum: General Help
---

### Post by Lord-Koga on 2009-11-01
I have Karmic Koala installed and fully updated.  For along time  now i've wanted to be able to play CoD2 on my laptop since it is the only computer I have capable of running it. But wine is not working to install it. It uses one cd (out of 6) to seemingly install the whole program. I have a copy of xp I want to use but since I have heard reconfiguring grub was a hassle i have procrastinated. So i was wondering if xp is hard to configure into grub after installing. And I have 2 partitions Partition 1 ext3 Main  install. Partition 2 = Swap Partition 3 will be for windows. When i reconfigure grub how to I do it with three partitions. How do i add windows to the list of operating systems to boot in.

---

### Post by Monotoko on 2009-11-01
This should help you:

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

I *think* that the grub-install command picks up Windows once it has been installed....that is only my assumtion though...could do with someone to verify it.

---

### Post by Lord-Koga on 2009-11-01
I will most certainly verify it when i install windows :)

---

### Post by Lord-Koga on 2009-11-01
What does it mean when it says sda6 is the boot partition I only have 2 partitions currently sda1 = ubuntu sda2 = extended sda5 swap sda5 and sda2 seem to be the exact same thing.

---

