---
title: "X in a mess (after using vgaswitcheroo?) can barely log in."
date: 2011-05-23
forum: General Help
---

### Post by kimangroo on 2011-05-23
I'm running Natty on a Sony VAIO SB with sandybridge i5 intel HD3000 and discrete ATI graphics.

Graphics have been working fine until I started playing around with vgaswitcheroo.

I turned off the discrete gfx (at least I think I did) and everything seemed fine.

However a little while later when I tried to reboot to ubuntu, X is completely messed up, 12 million little cursors all over the screen.

Booting to recovery mode is also touch and go. Depending on whether I have the physical gfx switch set to the internal gfx or not, sometimes I can get into a low graphics mode and sometimes not.

Once in the low graphics mode it is very buggy. I've tried to run vgaswitcheroo again, but when I try to turn the discrete gfx off again it stops working...

To be honest I don't know what is wrong, maybe it's not vgaswitcheroo but an update that didn't run again until I rebooted...

Does anyone know what might be wrong and what steps I can take to fix it?

---

### Post by TeoBigusGeekus on 2011-05-23
I'd try to delete the xorg.conf file - either from fallback mode or from a live medium - and see if I could boot up to a gui.

---

### Post by kimangroo on 2011-05-23
> **TeoBigusGeekus said:**
> I'd try to delete the xorg.conf file - either from fallback mode or from a live medium - and see if I could boot up to a gui.

Thanks for the reply. I seem to have a one in four success rate at booting ubuntu normally. When I say normally, in between the time from me selecting the normal boot in grub and the logon dialog appearing I just get a flashing white cursor on a black screen at the top left (or sometimes just a black screen) which isn't normal at all.

Right now I've been lucky and I'm in ubuntu with unity.

I checked Xorg.0.log for warning signs but didn't get much other than missing fonts and a resorting to old probe for vesa and fbdev.

Looked for a xorg.conf but don't seem to have one, only a xorg.conf.failsafe in etc/X11

I haven't installed any proprietary ATI drivers to my knowledge because I heard they didn't work with unity.

Other problems include an inability to start firefox because it says a firefox process is running already and vanishing battery indicators among other things. I guess these are seperate issues however.

---

