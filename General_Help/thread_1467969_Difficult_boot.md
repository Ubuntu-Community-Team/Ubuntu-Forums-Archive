---
title: "Difficult boot"
date: 2010-05-01
forum: General Help
---

### Post by MasterofTofu on 2010-05-01
Hey everyone,

I just got Ubuntu about two days ago and I love it! However, I am having a couple of issues with booting. I am running a 64-bit system (though I don't think it matters here), and here are my hard drives

30GB Kingston SSD (Windows 7 boot)
750GBx2 WD hard drives in RAID 0 (for games, personal files, music, etc.)
500GB WD hard drive (Ubuntu hard drive)
80GB Seagate external hard drive (misc stuff)

When installing Ubuntu, I chose my empty 500GB Western Digital hard drive as the install location of Ubuntu. When I was at the installation screen, it didn't detect my Windows 7 OS, which I thought was sort of weird.  The system booted fine, but I didn't get any prompt as to what OS I could select; it automatically booted my Ubuntu volume. I want to first be able to set Windows 7 as my default boot system, and then be able to choose which system I want to boot at start-up. Thanks!

---

### Post by dino99 on 2010-05-01
dont panic, that seems easy to fix into a terminal:

sudo grub-mkconfig && update-grub

---

### Post by MasterofTofu on 2010-05-01
Ok, so I went to boot my computer into Linux today and it wasn't booting at all! I just decided to format the hard drive and give it another go. But for some reason, when I try to boot it now, it gets stuck at the screen after the BIOS (verifying DMI pool data.........). Thankfully my Windows 7 boot is still working, but what is going on here? I didn't change anything in the BIOS. How can I get it to start back up?

---

### Post by MasterofTofu on 2010-05-03
Bump.

---

