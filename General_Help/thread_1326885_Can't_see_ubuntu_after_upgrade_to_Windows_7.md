---
title: "Can't see ubuntu after upgrade to Windows 7"
date: 2009-11-14
forum: General Help
---

### Post by akand074 on 2009-11-14
Hello,
I'm very confident this must have already been asked, but I couldn't seem to find it. Anyways I'll ask it anyways. I recently just updated my Windows Vista to Windows 7 and now it doesn't show ubuntu when I boot, it boots right into windows 7, does anyone know the fix to this?

---

### Post by aci016 on 2009-11-15
sorry not an answer but a question regarding upgrading windows 7? 

is your computer dual-booted? before the upgrade? how did you go about with the upgrade to windows 7??

---

### Post by rukiaEnix on 2009-11-15
When you say upgrading to Windows 7 you mean you upgrade from XP or Vista? and if so did you have GRUB as your boot loader? if yes then download supergrub it can be use as a boot cd or boot pendrive and it would repair your GRUB.
here is the official site:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Mark Phelps on 2009-11-15
> **akand074 said:**
> Hello,
I'm very confident this must have already been asked, but I couldn't seem to find it. Anyways I'll ask it anyways. I recently just updated my Windows Vista to Windows 7 and now it doesn't show ubuntu when I boot, it boots right into windows 7, does anyone know the fix to this?

When you did the upgrade, Windows 7 overwrote the MBR to remove the previous GRUB code.

But, you now have a choice:
1) Install EasyBCD to your Win7 setup and use it to add an entry to the Win7 loader for Ubuntu 9.10 -- leaving the Win7 MBR intact
2) Reinstall GRUB (or GRUB2), wiping out the Win7 entries, and then having to add entries to GRUB (or GRUB2) to get access to Win7 back.

The first can be done by going to the NeoSmart Technology forums, their EasyBCD support subforums, downloading the free software, and reading their tutorials.

The second depends on which GRUB version you have.  They are VERY different, and adding MS Windows entries is critically dependent on which version you have.

---

### Post by akand074 on 2009-11-16
I had windows vista before and then upgraded to windows 7, dual booting ubuntu karmic. Older versions of ubuntu used to have a simple system where I could just type "grub-update" when booted into the live cd and its back, but I think they removed it in the newer version. Would it not be a matter of just simply reinstall grub? what would be the easiest way to do that now?

---

### Post by ranch hand on 2009-11-16
If you are using 9.10 use these instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

---

### Post by akand074 on 2009-11-16
It worked! Thank you very much!

---

### Post by ranch hand on 2009-11-16
You may want to read the link in my sig.

---

