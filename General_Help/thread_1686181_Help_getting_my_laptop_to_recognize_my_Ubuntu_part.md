---
title: "Help getting my laptop to recognize my Ubuntu partition"
date: 2011-02-11
forum: General Help
---

### Post by Cyborg7 on 2011-02-11
Hello.

A while ago I successfully dual booted my system with Vista and Ubuntu. then Windows 7 came out and I wiped Vista off my laptop and installed Windows 7. The problem is that my laptop no long knows that there is a whole other operating system sitting on the hard disk and I can't access it. What can I do to fix this?

thank you very much

---

### Post by mikewhatever on 2011-02-11
You could reinstall Grub from the live cd/usb or user EasyBCD to manage the booting.
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD

Should work for all Ubuntu partitions, not just yours.;)

---

### Post by Cyborg7 on 2011-02-11
I no longer have the CD that I originally had, can I just download the GRUB or do I have to download everything all over again?

---

### Post by Hakunka-Matata on 2011-02-11
The bootloader Grub, or Grub2, modifies the MBR of the Windows installation drive.  Since you've installed a new windows system, you've probably removed the bootloader.  If you reinstall the bootloader, that may fix your system. Look at the link below:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Hakunka-Matata on 2011-02-11
@mikewhatever, sorry, there were no replies when I started mine............

---

### Post by Cyborg7 on 2011-02-11
Thanks for your help guys! I had to use EasyBCD to do it, now i need to reset my password because it's been too long and I'll be happily back in Ubuntu!

---

