---
title: "Geforce2mx driver?"
date: 2006-06-12
forum: General Help
---

### Post by greggh on 2006-06-12
I just installed Ubuntu. Which packages do I need to download and install to get 3d acceleration working? The guide says...

> 3D Nvidia Video Card Driver

No Nvidia Video cards have 3D acceleration enabled automatically with Ubuntu, because the manufacturer does not release open source drivers. However, it is possible to activate 3D acceleration. The process depends on which type of video card you have.

   1.

      If you have an older TNT, TNT2, TNT Ultra, GeForce1 or GeForce2 card, install the nvidia-glx-legacy and nvidia-settings packages from the Restricted repository (see Chapter 2, Adding, Removing and Updating Applications).
   2.

      Alternatively, if you have a newer card, install the nvidia-glx package from the Restricted repository (see Chapter 2, Adding, Removing and Updating Applications).
   3.

      To enable the new driver, run the following command in a terminal:

      sudo nvidia-glx-config enable 

   4.

      You may adjust the settings of the new drivers by running the application nvidia-settings (see the section called “Start a Program Manually”). If you wish, add a menu entry for this program (see the section called “Menu Editing”).

Is the Geforce2mx a legacy card the same as the Geforce2 and uses the nvidia-glx-legacy and nvidia-settings packages

or

is it one of the newer cards and uses the regular nvidia-glx package? Thanks for any help?

---

### Post by InsaneBeast on 2006-06-13
I think it depends on the specific MX card you have.  The list of supported cards  for the latest linux drivers, 1.0-8762, can be found at: [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

which lists support for:
```

GeForce2 MX 100/200 	0x0111
GeForce2 MX/MX 400 	0x0110

```

However, Gentoo's nvidia guide, [http://www.gentoo.org/doc/en/nvidia-guide.xml](http://www.gentoo.org/doc/en/nvidia-guide.xml),  lists one specific model, GeForce2 MX Integrated graphics, as an unsupported legacy product.

---

### Post by caserio on 2006-06-13
Hi,

Pick the nvidia-glx-legacy package.

---

### Post by mumushi on 2006-06-13
[QUOTE=caserio]Hi,

Pick the nvidia-glx-legacy package.[/QUOTE]
caserio is right :D

---

### Post by tseliot on 2006-06-13
This is the list of legacy cards:

```
NVIDIA chip name Device PCI ID
------------------------------- -------------------------------
RIVA TNT 0x0020
RIVA TNT2/TNT2 Pro 0x0028
RIVA TNT2 Ultra 0x0029
Vanta/Vanta LT 0x002C
RIVA TNT2 Model 64/Model 64 Pro 0x002D
Aladdin TNT2 0x00A0
GeForce 256 0x0100
GeForce DDR 0x0101
Quadro 0x0103
GeForce2 GTS/GeForce2 Pro 0x0150
GeForce2 Ti 0x0151
GeForce2 Ultra 0x0152
Quadro2 Pro 0x0153
```

In other words driver 8762 should work just fine.

---

### Post by mrvw0169 on 2006-06-13
I'm using nvidia-glx and I have a Geforce2 MX 400 and a 100 (or 200... I'm lazy to check) with no problems... I can play planetpenguin-racer now!

You can double check at the wiki: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
and check in "this list of cards" link in step 2... and the Geforce2 MX is in the top list...

And do you guys get a weird change in xorg.conf when running glx-config enable? It changes the video card's ID to ATI Radeon R[...]something (totally not important since it's just the identifier but just interesting)... I ended up just manually changing the Driver "nv" line to "nvidia" and all is well...

---

### Post by greggh on 2006-06-14
Thanks mrvw0169. It's confusing, but that list shows that while the Geforce2 is legacy, the Geforce2 MX uses the regular driver. That explains why I couldn't get it working with the legacy.

---

### Post by mrvw0169 on 2006-06-15
No problem and I agree that the list is confusing - I had to go through it twice to realize there were two sections on that page (I had thought it was one very long list for nvidia-glx due to so many cards listed without an obvious legacy distinction)...

---

