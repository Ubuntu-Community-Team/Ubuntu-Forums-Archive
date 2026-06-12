---
title: "Ubuntu not detecting both screens ..."
date: 2010-03-16
forum: General Help
---

### Post by wwsoft on 2010-03-16
hello ,  I am trying to set up dual monitors. I have a old nivida gforce card an a nice nivida chipset. I cannot get it to detect both or my monitors (2 big old CRTs).  I cant change the default video card in the bios from the card I put in to my decent chipset anyways how would I get Ubuntu to detect both monitors ?

---

### Post by wojox on 2010-03-16
You tried:

```
gksudo nvidia-settings
```

---

### Post by wwsoft on 2010-03-16
ya ... its a old card unsupported by the nivida util . Im complaining because nothing seems to be detecting the chip set with the card in.

---

### Post by scouser73 on 2010-03-16
> **wwsoft said:**
> hello ,  I am trying to set up dual monitors. I have a old nivida gforce card an a nice nivida chipset. I cannot get it to detect both or my monitors (2 big old CRTs).  I cant change the default video card in the bios from the card I put in to my decent chipset anyways how would I get Ubuntu to detect both monitors ?

Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by wwsoft on 2010-03-16
I already told you the gui is unsupported... My current Configuration file dose not work currently so It is blank , ie. It does _not_ work

---

### Post by lyall on 2010-03-16
see if this helps for 
Twin View
[https://help.ubuntu.com/community/XineramaHowTo]("https://help.ubuntu.com/community/XineramaHowTo")

**NvidiaMultiMonitors** [https://help.ubuntu.com/community/NvidiaMultiMonitors]("https://help.ubuntu.com/community/NvidiaMultiMonitors")

good luck and have fun learning

---

### Post by wwsoft on 2010-03-16
[I finally found drivers that work with card] its still not detecting the display plugged into the motherboard VGA port (2 graphics cards only one the on in PCI slot detected , chip-set ignored ...) how cn I get it to detect the chipset graphics card

---

### Post by lyall on 2010-03-16
> **wwsoft said:**
> [I finally found drivers that work with card] its still not detecting the display plugged into the motherboard VGA port. How do I get it to detect ? (2 graphics cards only one the on in PCI slot detected , chip-set ignored ...)

How are you connecting the Video cables?
are both connected to the Nvidia card?
or one the motherboard and one to the video card?

First try connecting only one video cable, just to the video card.
and boot your PC
then setup using the Nvidia
after you got it to work with the video cable, then connect the second video cable to the video card and use the instruction for Twin View and/or NvidiaMultiMonitors that I stated early

good luck and have fun learning

---

### Post by wwsoft on 2010-03-16
> **lyall said:**
> How are you connecting the Video cables?
are both connected to the Nvidia card?
or one the motherboard and one to the video card?

First try connecting only one video cable, just to the video card.
and boot your PC
then setup using the Nvidia
after you got it to work with the video cable, then connect the second video cable to the video card and use the instruction for Twin View and/or NvidiaMultiMonitors that I stated early

good luck and have fun learning

one video card = 1 vga slot
1 motherboard= 1 vga slot

I dont see how switching cables helps. the video card works , the motherboard chipset works , but how do I get both to work at the same time ? 

EDIT: Ill post a larger complaint later. [falling asleep]

---

