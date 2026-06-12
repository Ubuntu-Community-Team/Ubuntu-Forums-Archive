---
title: "Encrypted LVM password entry screen"
date: 2010-05-05
forum: General Help
---

### Post by Kakers on 2010-05-05
Hi guys,

Didn't know where to post this as it doesn't really call under desktop or installations haha.

Anyway, I have a bit of a problem. I've Installed Ubuntu 10.04 with and encrypted LVM password and it went on ok. When booting up the computer it comes to the screen where you enter your password to unlock the LVM which looks great.

However after installing the NVidia graphics driver for the laptop and rebooting, the LVM password entry screen seems to be too big to fit on the screen, not looking very good....

So my question is this... Is it possible to change the resolution for this screen?

---

### Post by Kakers on 2010-05-05
bump...

anyone? :(

---

### Post by cbraxton on 2010-05-05
I'm seeing the same effect with Nvidia on an encrypted system. After switching to the proprietary/binary driver the Ubuntu password entry screen has too low a resolution, though it does otherwise function OK. (Not sure why this happens since AFAIK this prompt comes up before X11 starts, using the video card in framebuffer mode.)

I also tried turning off the graphical boot screen, but messages keep scrolling on the console *after* the password prompt is given, which is kind of messy-looking and confusing. So I went back to the graphical boot. (The graphical boot display did not work at all in 9.04 with my video card, so this is actually something of an improvement.) 

Not a high-priority item but I'd agree it would be nice to be able to fix it.

---

### Post by atomicblue on 2010-05-11
This appears to be a regression as it was an adequate resolution on 9.10.  When typing the password, the password dots are not kerning correctly and sometimes cuts off half of the dot before with each subsequent letter.

I wonder if this is something that should be addressed by the papercut team (“Design and User Experience” ).  

[https://wiki.ubuntu.com/PaperCut](https://wiki.ubuntu.com/PaperCut)

I'm not sure I would call it a bug, per se, as the user is still able to log into the system and use it normally, but it definitely is an annoyance.

---

### Post by sin-tax on 2010-05-21
I'm having the same problem, vid card is a Radeon HD3500

---

### Post by peculiar penguin on 2010-05-21
No Nvidia anything here, but I had a similar issue with my ATI IGP (radeon driver and no KMS). Adding
```
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=1024x768
```to /etc/default/grub and running update-grub fixed it for me. You may have to experiment with the resolution, my display's native one (1280x800) didn't work.

---

