---
title: "Have Acer Aspire one netbook want to install ubuntu  via wubi"
date: 2009-11-11
forum: General Help
---

### Post by Babydoll25 on 2009-11-11
I have an acer aspire one with 1Gb RAM and 160 Gb hard drive. I am running win xp. I would like to install ubuntu 9.10 via wubi. Can I? Im sick of windows

---

### Post by ubiedubie on 2009-11-12
I have just tried to install Ubuntu 9.10 Netbook Remix using Wubi on my Acer Aspire One Pro.

After rebooting I tried to boot Ubuntu and it started like this:
[linux-bzimage setup=0x3400 size=0x3b26e0]
[Initrd, addr=0x37864000, size=0x78b7af]

Then stopped doing anything.. I restarted to try again and the same happened.

I tried again with safe graphics mode and the same thing happened. I then uninstalled Wubi :sad:

So from me, for the netbook ubuntu at least - its a no. (I imagine the desktop ubuntu would be a no also considering the netbook remix is merely an alternative desktop environment)

If anyone knows how I can get it to work it will be great :p

I don't want to install it to the hard drive because it detects my partitions totally incorrectly so Grub will be really messed up. It thinks my recovery partition is Windows Vista (its actually XP pro). It also believes my Windows XP partition is Windows 7. It thinks my Windows 7 partition is a data partition.

I know I can edit grub - but if you edit grub, when you update your kernel it goes nuts saying the grub settings have changed. Then the update messes up.

---

