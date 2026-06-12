---
title: "X problem after driver installation."
date: 2010-10-21
forum: General Help
---

### Post by JuliusRaphael on 2010-10-21
Hi! 

Im a Ubuntu newbie and I've just tried to install some drivers for my GeForce 8400. But when I rebooted my screen got black so I rebooted into recovery mode and got to the "DOS-mode". I tried to type "startx" and got this message:

EE Failed to load /usr/lib/xorg/extra-modules/libglx.so
EE Failed to load module "glx" (loader filed, 7)
EE Failed to load module "nouveau" (module does not exist, 0)
EE open /dev/fb0: No such file or directory
EE NV(0): No valid initial configuration found
EE Screen(s) found, but none have usable configuration


So how can I fix this problem? I use Ubuntu 10.10 I've tried everything I know(which is very little btw) and nothing did work.

Plz help me! I don't have a clue what to do.

/J

EDIT: I tried reinstalling the drivers and it now says:

the NVIDIA kernel module has the version 260.19.06 but this NVIDIA driver componet has version 260.19.12. Please make sure that the kernel module and all NVIDIA driver componentes have the same version.
EE Failed to initialize the NVIDIA kernel module. Please see the systems's kernel log for additional error messages and consult the NVIDIA README for details.
EE ***Aborting***
EE Screen(s) found, but none have a usable configuariton.

Fatal server error:
no screens found

---

### Post by JuliusRaphael on 2010-10-21
Someone?

---

### Post by Tobeus on 2010-11-18
I'm getting the same issue on 10.10 after nvidia current drivers were installed using an 8400gs pcie card.  Wish I had an answer for you, but no matter how much searching I seem to do, nobody seems to have the correct answer.  I have tried canonical's different nvidia drivers, nvidia's downloadable drivers, and even nouveau (original open source) drivers, but no luck.  I've ordered a new ATI card to see if I can get things running with a new card, but I'm not sure what the deal is.

I hope you have more luck than I have had.  Good luck!

---

### Post by Tobeus on 2010-11-18
I don't think this is going to help you, but from the command line, try typing
```
sudo nvidia-xconfig
```
then restart by typing
```
sudo reboot
```
Again, I don't think this will get you into X, but it is worth a try.

---

