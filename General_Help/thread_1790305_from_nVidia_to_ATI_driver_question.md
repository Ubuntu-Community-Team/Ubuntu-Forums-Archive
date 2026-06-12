---
title: "from nVidia to ATI driver question"
date: 2011-06-24
forum: General Help
---

### Post by tpprynn on 2011-06-24
I am about to buy an ATI Radeon 4650 card, nothing flash or expensive but double what I've paid before and I've seen it is used in some current commercially available Ubuntu systems and therefore a safe bet. 

I just wanted to get clued up beforehand about drivers. Am I supposed to uninstall my onboard nVidia chip's drivers first or just fit the card, boot up and add the ATI one? There won't be any clashes or issues if the nVidia driver is left?

If it's relevent, at the moment I'm connected to my monitor by vga, but will resume using the digital slot when I have the card.

Thank you.

---

### Post by Herman on 2011-06-25
It would probably make things a little easier if you remove the nVidia drivers before you shut down to fit the ATI card. 
On reboot it will then boot with the default drivers so you'll at least  have a display and then you can install the ATI proprietary driver.

If you forget you might boot to a black screen, but don't worry, you can reboot and go into 'recovery mode' and fix the xserver from menus in there.
Another way to fix it is to boot a live CD or USB and go into your HDD Ubuntu and delete your /etc/X11/xorg.conf which is the file that tells Ubuntu to use whichever video card driver you used last.  As long as you know what to do in advance it won't be a big problem. When you reboot without any /etc/X11/xorg.conf, Ubuntu will fall back on the default video drivers which will give you a pretty good display until you get around to installing the ATI proprietary driver.

---

### Post by tpprynn on 2011-06-28
Thanks.

---

### Post by WorMzy on 2011-06-28
You /shouldn't/ have any problems if you don't remove the nvidia driver before installing the ATi card; your new graphics card should be detected when you boot up, and the correct module should be loaded for it.

Uninstalling the nvidia driver beforehand isn't a bad either though.

---

### Post by tpprynn on 2011-06-30
In the end it was a bit of a mess I think, but I have settled with the open source driver after a fresh install rather than sort out the properietary driver's stutterings, and the free driver seems smoother to me, though there are very occasional artefacts. I'll look into any tweaks that can be done at a later date after a holiday.

('Hot Tip': I bought the 4550 in the end, for 21 quid, new, plenty adequate for a non-gamer. There are a pile on eBay right now by XFX, half price becuause I think the bracket is ever so slightly warped - it just meant a slight amount of perspiration during the fitting.)

---

