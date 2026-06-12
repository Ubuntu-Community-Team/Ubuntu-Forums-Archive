---
title: "Screen starts to blink"
date: 2010-09-17
forum: General Help
---

### Post by Tatzka on 2010-09-17
Hi,
I got my first experience today to ubuntu, It installed (imo) properly from boot cd.
But now sometimes screen blinks once, gives these codes:
*speech-dispatcher configured for user sessions
*starting common unix printing system: cupsd
Pulse audio configured for per-user sessions
*enabling additional executable binary formats binfmt support
*checking battery state
This stays a little while and after that screen starts to blink, and i have to reboot computer.
I dunno how to fix this :S

---

### Post by TroN-0074 on 2010-09-17
I did this
> 
                                                  Other graphics card users including nVidia may get a black screen  with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801")
One fix for this is to create this file.
         Code:```


            gksu gedit /etc/initramfs-tools/conf.d/splash 
``` and add this option FRAMEBUFFER=y, save the file.
Then
          Code:```


          sudo update-initramfs -u
```

---

### Post by Tatzka on 2010-09-17
Thank You Sir, I think that I did it right. ALT+F2, the code 1, then add that option code to it, save, and ALT+F2 & second code.

---

### Post by TroN-0074 on 2010-09-17
Yes! It did it for me, let us know if it worked for you.

---

### Post by Tatzka on 2010-09-19
No, it still starts to blink :/ it usually does that if I'm starting to install something..

Oh, btw my graphics card is Intel 82845G/GL/GE
Subsystem is Intel Corporation Device 5247 but dunno if its necessary

---

