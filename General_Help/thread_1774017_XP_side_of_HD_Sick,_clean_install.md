---
title: "XP side of HD Sick, clean install?"
date: 2011-06-02
forum: General Help
---

### Post by oldtug on 2011-06-02
Need help advice, 

Running Dual Boot  with 10.04 Lucid Lynx and XP.  Recently shut down computer and unhooked all connections and when hooked up again, now **XP will not boot :frown:**.   Ubuntu boots and runs fine.  XP just keeps hanging during boot and restarts, I have tried to get it going almost every way, up to safe mode, doing a repair reinstall of xp and resetting bios. Nothing working.  I have been able to save files through access from Ubuntu partition.  I really don't want to completely wipe the XP partition, but it's looking like I may have to do a clean install and loose everything, but...

my questions?

First, have I missed any way to try to get XP to boot?  

2nd,
Can I just do a clean install on the XP partition without disturbing the Ubuntu partition or the dual boot process?  I don't want to loose the other half of my computer in process.  
What is best method to restore the XP side

And yes, I know I could/should dump the xp all together, but just can't do it right now

Thanks for all your help

Eric
Seattle

---

### Post by TeoBigusGeekus on 2011-06-03
I don't know how to repair xp, but if you do an xp re-installation, windows will overwrite grub2.
To reinstall it, see [this]("https://help.ubuntu.com/community/Grub2#METHOD 3 - CHROOT").

---

