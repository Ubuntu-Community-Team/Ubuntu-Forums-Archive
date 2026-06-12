---
title: "Reboot and select proper boot device or insert boot media in selected boot device ..."
date: 2011-12-24
forum: General Help
---

### Post by Acaldeira on 2011-12-24
Hello,

I decided to give Ubuntu 11.10 a go and downloaded the .iso from the ubuntu website. I got it into my usb pen and i was able to install the OS with no problem. But when i rebooted it gave me this error message:

**Reboot and select proper boot device or insert boot media in selected boot device and press a key**



Can anyone help me? I already installed ubuntu three times and i always get the same error.

---

### Post by dandnsmith on 2011-12-24
I suspect that you've installed the bootloader to the 'wrong' place.
If you consult [this site](http://sourceforge.net/projects/bootinfoscript/), download the script and run it, the posted results may help someone here to diagnose the problem.

I cannot remember whether this is the install process which, I found to my disgust, doesn't seem to allow you to not install the bootloader (which is what I wished to do at the time).

---

### Post by bobsageek on 2011-12-24
Do you have a newer PC, like very recent? Many newer PCs are shipping with UEFI firmware in place of traditional BIOS and you may need to take a couple extra steps. My Acer X1930 ships with UEFI and while Ubuntu works like a champ I had to do several extra things to get Fedora 16 running, but it is doable.

---

### Post by Acaldeira on 2011-12-24
> **bobsageek said:**
> Do you have a newer PC, like very recent? Many newer PCs are shipping with UEFI firmware in place of traditional BIOS and you may need to take a couple extra steps. My Acer X1930 ships with UEFI and while Ubuntu works like a champ I had to do several extra things to get Fedora 16 running, but it is doable.

Hello, yes my Laptob is new, it has only two months.

Here are the speccs:

AMD® Fusion APU E450 1.65GHz (dual core)
AMD® Radeon HD 6320/
DDR3, 2 x SO-DIMM, 4GB
2.5" SATA 500GB HDD


Asus 1215b

---

### Post by dandnsmith on 2011-12-24
OK, so thats the CPU and graphics - but nothing about the PC model to allow checking on UEFI

---

### Post by Acaldeira on 2011-12-24
> **dandnsmith said:**
> OK, so thats the CPU and graphics - but nothing about the PC model to allow checking on UEFI


How do i check that? :)

---

### Post by dandnsmith on 2011-12-26
If you're saying you have Asus Eee PC 1215B, then I can find reviews and brief hardware specs and suggestion that it is sold with Win7 installed - but nothing the indicate whether there is a UEFI type BIOS

[this site](http://www.tested.com/news/how-to-check-if-your-pc-is-uefi-ready-for-windows-8/2895/) suggests you can test if it has UEFI, which with it being a recent Asus seems likely, and running gparted from a LiveCD with ubuntu can show whether the HDD is UEFI partitioned.

---

