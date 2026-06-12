---
title: "Installation of Ubuntu 11.04 does not work"
date: 2011-09-14
forum: General Help
---

### Post by U2XS on 2011-09-14
I went to Ubuntu.com and downloaded the latest stable version (11.04).  I went through the setup - which always shows a stylish improvement over the last - and it seemed to install fine.  When I start up, it shows the following (image below).  I cannot get past this screen.  The only issue that I can see is this: 
> Stopping automatic crash report generation		[fail]

Beyond that, I have tried booting into the recovery section, updating, upgrading, etc.  I've tried installing it again over the partition (this time without including updates as it installs) and again, I have the same issue.  Does anyone know what it could be or how I can fix it?

[IMG]http://img193.imageshack.us/img193/1503/img00188c.jpg[/IMG]

---

### Post by Basher101 on 2011-09-14
okay once you get into Grub (your bootloader with the purple background) press "e" when you have the uppermost option highlighted (Ubuntu) and then write to the text at the end with a space before this:```
nomodeset
``` and press ctrl+x to boot with that small change we just made. This is only a temporary fix so if you have to reboot again you must do this over and over again. I will explain on a permanent fix if this solves your prior issue and you are able to log into Ubuntu

---

### Post by U2XS on 2011-09-14
Unfortunately the results are the same.  If I put it in it's own line (within or after) the other information, it tells me that there is an unknown command and that I should press any key to continue.

When I place it at the end of the last line, the screen flickers a few times, but ultimately it takes me to the same error message.

---

