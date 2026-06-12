---
title: "Ubuntu 9.10 not finding Windows"
date: 2009-12-07
forum: General Help
---

### Post by HalfDemon1122 on 2009-12-07
So today I decided to install Ubuntu 9.10 onto an old 40gb IDE harddrive I had lying around. I've used it for ubuntu before, but now I decided to run it along side my SATA 320gb with windows vista on it. Well the installation went fine, but when I decided I wanted to go back into vista, I turned off the computer, unplugged the 40gb, and booted back up. Suddenly it went into the GRUB loader, and went into rescue mode from "no disc".

The disc is showing up on BIOS, and even on ubuntu, but when I try to access it, it gives me an "Unable to mount" error. 

Is this a GRUB error, or rather is something wrong with my HDD?

---

### Post by Sin@Sin-Sacrifice on 2009-12-07
You wrote over the MBR on the first disk. You should be able to dual boot without removing the 40GB disk. Just leave it in and Windows should be in the grub menu. If it's not then you're going to need to add it to grub.cfg and that you can learn to do from a Google search.

---

### Post by HalfDemon1122 on 2009-12-07
Its not on the boot menu, and I have NO idea how to edit grub.cfg, or even where to look (sorry i'm a bit of a beginner with ubuntu)

---

### Post by Sin@Sin-Sacrifice on 2009-12-07
[I assume you know how to use Google...]("http://ubuntuforums.org/showthread.php?t=1195275")

---

