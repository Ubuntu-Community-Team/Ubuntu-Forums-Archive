---
title: "Grub - Wrong menu, can't boot Ubuntu (dual boot with XP)"
date: 2011-04-29
forum: General Help
---

### Post by IGITIHI on 2011-04-29
I have a hard drive with 4 partitions:
1)Win XP (40GB)
2)Linux Home(?) Partition (107MB)
3)Linux (30GB)
4)Linux swap

Initially, my system worked fine as dual-boot. Recently I had to reinstall Win XP. After doing so, of course I couldn't boot in Ubuntu anymore. I used Super Grub Disk to restore the original mbr but I obviously did something wrong. I got grub back but the new menu points to older kernels that don't exist anymore. I have Ubuntu 9.10 but the menu points to 8.04 and can't boot.

However, I can use Super Grub Disk CD to boot directly to 9.10 and everything works fine. I ran "sudo grub-update" from the terminal but, again, I got the wrong boot menu. 

So, since my Linux installation is unharmed, I suppose there is a way to rebuild the grub menu and get everything back to normal. Ideas please?

Edit: I just noticed that the small Linux partition (number 3) two grub folders. One in "boot" folder and one in root. Could that be the problem?

---

