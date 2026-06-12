---
title: "Change &quot;Primary&quot; OS - XP/Ubuntu"
date: 2009-12-22
forum: General Help
---

### Post by manco on 2009-12-22
Hey everyone!  I'm a Ubuntu noob but a decent computer guy, so here goes.

After getting tired of Windows, I've decided to try Ubuntu in a Dual-Boot.

It's going to be on my Family's computer, which is perfect because it's only used for Email/Microsoft Office stuff anyway (plus, no viruses!)

Currently, I'm installing Windows XP on the PC fresh, and then I will go in afterwards and install Ubuntu 9.10 on a new partition.

Here's my question:

If I recall correctly, my PC will still boot to Windows by default if I don't select Ubuntu in time during boot.

Is there any way for my PC to reverse this? (meaning, boot into Ubuntu by default if I don't choose to boot into XP or something)

Thanks!

---

### Post by synapsys on 2009-12-22
> **yellowsnow4free said:**
> 
If I recall correctly, my PC will still boot to Windows by default if I don't select Ubuntu in time during boot.

Is there any way for my PC to reverse this? (meaning, boot into Ubuntu by default if I don't choose to boot into XP or something)

Thanks!

If you install ubuntu second, it will install grub (bootloader) to your mbr. When your computer boots, grub will give you a choice whether to boot ubuntu or windows, ubuntu being the default. To change this, you can install startupmanager on ubuntu and choose the default operating system.

---

### Post by manco on 2009-12-22
Cool!  That's what I was hoping for.

Thanks!

---

