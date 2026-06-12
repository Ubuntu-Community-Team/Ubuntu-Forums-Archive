---
title: "Bootloader to boot from eSATA"
date: 2011-09-09
forum: General Help
---

### Post by shinnyx on 2011-09-09
Hi all, I'm trying to install ubuntu on a eSATA external hardisk. The eSATA hardisk can be detected during the installation (with live usb), however, the laptop (hp dv4) doesn't support boot from eSATA.

So, my question is is that possible to boot from eSATA without the BIOS support? For example, boot from internal hardisk where the bootloader located, and let the bootloader detect the eSATA (ubuntu is installed in the hardisk). Thanks!

---

### Post by Basher101 on 2011-09-09
Yes this is very possible (dunno if it will work without BIOS support tho). I got my Grub on my internal HDD (/dev/sda) and it has detected my Fedora 15 installation on my USB stick. I can boot like this either to Ubuntu on my internal hdd, windows on my internal or fedora on the usb stick. You should try tho. But before you install the bootloader on your internal hard disk, make sure you make a Recovery CD for windows first so you can restore the original MBR if necessary.

---

### Post by Grenage on 2011-09-09
Yes, I think it should work.  If you've got Grub on an internal disc, you should be able to reference the eSATA drive.  Someone else here is bound to have tried this.  Hell, you could even install grub on a USB thumbdrive and use that instead of a mechanical drive.

---

### Post by Basher101 on 2011-09-09
I also have grub and an entire fresh install of Ubuntu on my external hard disk so i can do some recovery in case somehow my system should screw up.

---

### Post by zero2xiii on 2011-09-09
It can work.

I have a dual installation of Ubuntu 11.04 and 10.04 studio on my notebook, and then on a eSATA drive I have a dual boot of win 7 and win XP.

TO boot from the eSATA drive I just hit F12 during startup (boot device key). Then select the eSATA drive as the boot device instead of my internal drive.. 

;) Cherz

---

### Post by Basher101 on 2011-09-09
Uhm you have BIOS support then, he does not. I think the OP should just try and see if it works. If it does, congratz to you sir, if not, too bad.

---

