---
title: "How do I disable restricted graphics drivers?"
date: 2009-12-24
forum: General Help
---

### Post by maxrpowell on 2009-12-24
So, my kubuntu installation worked fine until I installed my restricted ati driver through the hardware driver utility. Now i restart my computer, I hear all the start up sounds but my screen shows nothing other than the blue ' Check Connection Cable' box that dances around the screen. **_I just want to know how to disable the ati driver through the command prompt_**.Thanks for your help.

---

### Post by coffeecat on 2009-12-24
I presume you're using 9.10, Karmic Koala. Rename the xorg.conf file that the fglrx installer probably created. If you have no xorg.conf file in Karmic, the xserver will autodetect all hardware and use the open-source driver.

From a command prompt:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.disabled
```... or whatever you want to call it. Then reboot.

Better to rename it rather than delete it in case you need to see what's inside.

---

### Post by maxrpowell on 2009-12-24
thanks, i will try it right now

---

### Post by maxrpowell on 2009-12-24
well, it says that the file doesn't exist, i believe i'll go back to 9.04 becuase it always worked well for me.

---

### Post by coffeecat on 2009-12-24
> **coffeecat said:**
> ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.disabled
```

> **maxrpowell said:**
> well, it says that the file doesn't exist, i believe i'll go back to 9.04 becuase it always worked well for me.

Before you go back to 9.04, double-check you didn't make a typo. Don't forget, Linux is case-sensitive. See the capital and lower-case X characters in that code. And X11 = CAPITAL-X 11 (eleven). Also, just to make sure... from the command line:

```
cd /etc/X11
ls xorg*
```

---

### Post by maxrpowell on 2009-12-24
thanks, that worked! i guess i did make a typo! does anyone know what the problem with the ati driver is? is there any way to make it work, anything with graphics is slow without it. i can live without it though.

---

### Post by coffeecat on 2009-12-24
I have a laptop with an ATI graphics chipset and installed the proprietary fglrx driver. Disaster! From what I understand, ATI/AMD are dilatory with releasing new versions of their proprietary driver, and the current version of the fglrx driver is incompatible with the version of the xserver used in Karmic. The reason you were OK in Jaunty is that it has an older version of xserver and possibly an older version of the fglrx driver, both compatible with each other.

I believe that the open-source ati/radeon driver is a better long-term option anyway. I've seen some threads where people have installed the latest and bleeding-edge greatest from a PPA repo and are pleased. I'm hoping for better things in Lucid. At the moment, ATI graphics in Lucid Alpha 1 is no better than in Karmic with the open-source driver (at least on my graphics chipset), but there are several months to go in the development process. I'm keeping my fingers crossed. I haven't had the time or opportunity to experiment with the bleeding-edge stuff in Karmic yet.

---

### Post by maxrpowell on 2009-12-24
Ok, good to know its not just me. I guess I'll just do without. And make sure my next computer doesn't have ATI chips.

---

### Post by coffeecat on 2009-12-24
> **maxrpowell said:**
>  And make sure my next computer doesn't have ATI chips.

Wise choice. :)

One thing I forgot. Now you have a GUI again, you'll probably want to uninstall the fglrx driver package(s). If they get updated they might get re-activated. Have a look for xorg-driver-fglrx - that's the one. When I'm next in my ATI-graphics laptop, I'll look in my logs and see if there were any other packages I took out when I disabled the fglrx driver.

---

### Post by coffeecat on 2009-12-24
In fact I had a useful bookmark:

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

You need to remove:

xorg-driver-fglrx
fglrx-amdcccle
fglrx-kernel-source
xorg-driver-fglrx-dev

---

