---
title: "Failed to install with Windows 7"
date: 2009-11-14
forum: General Help
---

### Post by Venomrush on 2009-11-14
I have installed ubuntu using wubi.
After installation, it asks to restart. I booted into ubuntu but without any success.
See - [http://twitpic.com/os6px](http://twitpic.com/os6px)

I booted back into Windows and saw that ubuntu-9.10-desk-amd64.iso is there in /ubuntu/install/

I tried again but this time using the ISO file instead.
Same error saying /ubuntu/install/installation.iso does not exists, I booted back into Windows and the installation.iso is there where it should be!!!

Please advise a solution.

I am using Windows 7 Ultimate 32-bit, installed from clean onto HP dv7-1135ea laptop, specs can be found at [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01561365&tmp_task=prodinfoCategory&lc=en&dlc=&cc=us&product=3816595&lang=](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01561365&tmp_task=prodinfoCategory&lc=en&dlc=&cc=us&product=3816595&lang=)

---

### Post by Mark Phelps on 2009-11-14
There don't appear to be solutions to this.  

Apparently, the combination of the new partitioning scheme with Windows 7 and the new GRUB2 is presenting problems with booting into Ubuntu when installed via Wubi.

---

### Post by Xog on 2009-11-14
> **Venomrush said:**
> I have installed ubuntu using wubi.
After installation, it asks to restart. I booted into ubuntu but without any success.
See - [http://twitpic.com/os6px](http://twitpic.com/os6px)

I booted back into Windows and saw that ubuntu-9.10-desk-amd64.iso is there in /ubuntu/install/

I tried again but this time using the ISO file instead.
Same error saying /ubuntu/install/installation.iso does not exists, I booted back into Windows and the installation.iso is there where it should be!!!

Please advise a solution.

I am using Windows 7 Ultimate 32-bit, installed from clean onto HP dv7-1135ea laptop, specs can be found at [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01561365&tmp_task=prodinfoCategory&lc=en&dlc=&cc=us&product=3816595&lang=](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01561365&tmp_task=prodinfoCategory&lc=en&dlc=&cc=us&product=3816595&lang=)

did you check the MD5 hash after downloading the ISO?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I had to wind up downloading it 3 times to get flawless files :P

---

### Post by lindsay7 on 2009-11-14
> **Venomrush said:**
> I have installed ubuntu using wubi.
After installation, it asks to restart. I booted into ubuntu but without any success.
See - [http://twitpic.com/os6px](http://twitpic.com/os6px)

I booted back into Windows and saw that ubuntu-9.10-desk-amd64.iso is there in /ubuntu/install/

I tried again but this time using the ISO file instead.
Same error saying /ubuntu/install/installation.iso does not exists, I booted back into Windows and the installation.iso is there where it should be!!!

Please advise a solution.

I am using Windows 7 Ultimate 32-bit, installed from clean onto HP dv7-1135ea laptop, specs can be found at [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01561365&tmp_task=prodinfoCategory&lc=en&dlc=&cc=us&product=3816595&lang=](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01561365&tmp_task=prodinfoCategory&lc=en&dlc=&cc=us&product=3816595&lang=)

You said I booted back into Windows and saw that ubuntu-9.10-desk-amd64.iso is there in /ubuntu/install/

but, you also said  I am using Windows 7 Ultimate 32-bit


I do not know if you can mix and match 64 bit and 32 bit systems with wubi.

---

### Post by Venomrush on 2009-11-15
> **lindsay7 said:**
> You said I booted back into Windows and saw that ubuntu-9.10-desk-amd64.iso is there in /ubuntu/install/

but, you also said  I am using Windows 7 Ultimate 32-bit


I do not know if you can mix and match 64 bit and 32 bit systems with wubi.

That's correct.
I have no idea why Wubi downloaded 64 bit when I'm clearly running 32 bit.
I ran wubi in Win 7 32 bit.
Restarted and got that error, it seems wubi downloaded 64 bit for some apparent reason.

---

### Post by Venomrush on 2009-11-15
> **Xog said:**
> did you check the MD5 hash after downloading the ISO?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I had to wind up downloading it 3 times to get flawless files :P

The MD5 hash is correct.

---

### Post by Mark Phelps on 2009-11-15
I know in the case of MS Windows OS's, you can install either 32-bit or 64-bit on a 64-bit processor box, but you can install only the 32-bit OS on a 32-bit processor box.

Don't know if Ubuntu has the same restrictions.

---

### Post by 3rdalbum on 2009-11-15
There is no problem with using Wubi to get a 64-bit version of the distro when you are running 32-bit Windows. The computer only runs one operating system at a time, and the currently-running one doesn't care what bit-width the other one(s) are.

I don't know what the problem is, but the best solution/workaround is to boot from the Ubuntu CD and do a real dual-boot installation. Far fewer limitations, far less that can go wrong. Just make sure you back up all your data first.

---

### Post by A_T on 2009-11-15
Wubi won't work properly with the Windows 7 bootloader.

---

### Post by Venomrush on 2009-11-15
Thanks for all the responses, the thing is even try installing using the full ISO image, not through wubi, that didn't work neither.

---

### Post by ArinSky on 2009-11-15
did it just not show up? or did it fail to install?

if its not showing up, you have to make grub work... windows 7 boot defaults, so you have to use liveboot and install grub, then add windows to the end.

---

### Post by wilee-nilee on 2009-11-15
> **Venomrush said:**
> Thanks for all the responses, the thing is even try installing using the full ISO image, not through wubi, that didn't work neither.

Post exactly what you tried and what you have done with the wubi install and if the Windows boot still shows Ubuntu from the wubi even if removed.

Since your having some troubles you may want to ask some questions before your try more installing. ;)

W7 shouldn't still have the boot if Ubuntu installed but anything is possible. If you can take a screen shot of the partitions that would be helpful.

---

### Post by Venomrush on 2009-11-16
> **ArinSky said:**
> did it just not show up? or did it fail to install?

if its not showing up, you have to make grub work... windows 7 boot defaults, so you have to use liveboot and install grub, then add windows to the end.

It shows up with options to boot into Windows 7 or Ubuntu, I chose the Ubuntu and it's stuck there, seems like it was unable to install.

Here is the screenshot [http://www.twitpic.com/os6px](http://www.twitpic.com/os6px)

---

