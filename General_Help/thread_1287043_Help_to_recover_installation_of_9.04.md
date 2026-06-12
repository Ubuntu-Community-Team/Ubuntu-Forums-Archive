---
title: "Help to recover installation of 9.04"
date: 2009-10-09
forum: General Help
---

### Post by ashto on 2009-10-09
Hi, I am new to the world of Ubuntu and Linux.  Two weeks ago I installed 9.04 on an external hard disk that has been working fine, and has been a real pleasure compared to Vista.  
However now when I try to boot, the system fails before I get to the user screen, but after I see the Ubuntu logo. 
When I run Ubuntu from the live cd, and have my external drive plugged into my laptop and I can explore all the files on it so it does not look like the hdd has failed?  

I have tried to read the forums to see if there is a way to repair my installation but I have had no success and would welcome any advice how to make my HDD boot again? 
Thanks

---

### Post by mgol on 2009-10-09
I assume You didn't change Your bootloader disk location during the install? If You install an OS on an external drive, it's better to put the bootloader on it and to boot from USB if You want to run that system.

Press 'e' letter in GRUB menu and erase 'quiet' and 'splash' options from the line; then write down here what happens when the boot stucks (You can take a picture).

---

### Post by ashto on 2009-10-10
Thanks mgol for the reply,

Grub is installed to the external drive.  I took your advice and deleted 'quiet' from the grub options,  the only reference to 'splash' I could find was at the end of the kernel line so I deleted this as well ('ro quiet splash'), I hope this is what you meant?

When the system booted it reached the same point as before then stopped.  I have attached a photo that shows, the black screen and distorted ubuntu logo across the top.

---

### Post by DeMus on 2009-10-10
> **ashto said:**
> Thanks mgol for the reply,

Grub is installed to the external drive.  I took your advice and deleted 'quiet' from the grub options,  the only reference to 'splash' I could find was at the end of the kernel line so I deleted this as well ('ro quiet splash'), I hope this is what you meant?

When the system booted it reached the same point as before then stopped.  I have attached a photo that shows, the black screen and distorted ubuntu logo across the top.

Although I can't see the distorted Ubuntu logo, I believe you have a problem with your video driver. Did you install a new version and this was the first time you (re)booted?
Try to boot in safe mode, normally 2nd choice in the grub menu. See if that works.

---

### Post by ashto on 2009-10-10
Hi, I have not changed the video driver?  I had installed a pdf editor and changed my desktop theme before my last reboot.

When you say safeboot do you mean 'Recovery Mode'?  If yes, I have tried this and used various recovery options but I always recieve the same problem when I reboot.

Not sure if this is relevant but I use the external hdd on two different laptops (an acer aspire 5630 & HP6930p) and recieve the same problem.

---

### Post by mikewhatever on 2009-10-10
> **ashto said:**
> Hi, I have not changed the video driver?  I had installed a pdf editor and changed my desktop theme before my last reboot.
.......

Do you know which theme? Was is one from the preinstalled selection or a third party one?

---

