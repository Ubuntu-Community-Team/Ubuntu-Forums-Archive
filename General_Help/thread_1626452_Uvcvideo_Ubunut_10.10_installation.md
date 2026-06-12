---
title: "Uvcvideo Ubunut 10.10 installation"
date: 2010-11-20
forum: General Help
---

### Post by tauh on 2010-11-20
I am trying to install Ubuntu 10.10 and i get this error message after a while of loading:

[   94.634959] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26) 
[   94.634977] uvcvideo: Failed to initialize the device (-5)

What does it mean? How do i fix it?

Thanks!

And yes i mean Ubuntu and not Ubunut (title). ;)

---

### Post by tauh on 2010-11-21
I managed to install Ubuntu using the alternate install. But i still get the error message during boot of Ubuntu.

I googled uvcvideo and it turns out to be a problem with the the webcam and its drivers. Can i disable the cam and its driver?

I tried to disable using the bios but there isn't any "driver"/"Components" disable alternative.

Grub works fine and i can boot Windows 7.

---

### Post by Arminho on 2010-11-26
Hi!
I'm having similar problems with Ubuntu 10.10 on my Asus laptop with an integrated webcam.
It worked fine in Ubuntu's previous version 10.04.
Since uvcvideo is part of the linux kernel, you may use a different kernel version. I don't know if it's possible to get a 10.10 installer with different kernel version, but you may install 10.4. and wait with the upgrade to 10.10 until the problem is solved.

I don't know if it's possible to disable your webcam in bios. Why you want to do it? Does Ubuntu fail during boot because of this problem?

---

