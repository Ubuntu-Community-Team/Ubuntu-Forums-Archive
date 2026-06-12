---
title: "Ubuntu 9.10 graphics problem"
date: 2010-01-21
forum: General Help
---

### Post by Mthbk1 on 2010-01-21
After installing the fresh copy of ubuntu, my pc is unable to detect the highest resolution of the monitor. Any idea?

---

### Post by mörgæs on 2010-01-21
No :-) not until you tell a little more about your graphics card. Could you please post the output from ```
hwinfo --gfxcard
``` ?

---

### Post by TBABill on 2010-01-22
You did not mention whether you enabled the non-free repositories in Ubuntu so I assume you need to first take that step in order for the system to download the appropriate video card driver for your card (if available). The standard driver will not allow the highest settings in most cards because they usually require the proprietary driver (nVidia, ATI, etc.).

---

### Post by Grenage on 2010-01-22
> After installing the fresh copy of ubuntu, my pc is unable to detect the highest resolution of the monitor. Any idea?

It's most likely yet another EDID issue; this is usually down to a bad monitor cable, or general glitch.  I wrote a rough guide on manually specifying resolutions the other day, you can find it [here]("http://www.grenage.com/xorg.html").  Failing that, come back and give us the following information:

Your monitor make and model.
The result of:

```
lspci | grep VGA
```

---

### Post by efflandt on 2010-01-22
Even if your card is supported by standard video modules, X might not use an optimum or native mode when connected by VGA.  I depends what it recognizes and matches up for capabilities of your video card and monitor.  It may also depend upon amount of video RAM.  /var/log/Xorg.0.log may give a clue what modes X sees and why it does not use some.  Multiple displays (like laptop with external VGA) might also limit automatic modes.

I have not tried HDMI, but in my case switching to DVI, X automatically recognized and used the native 1280x720 mode of an older 27" HDTV Ready LCD that defaulted to an odd stretched 4:3 mode when connected with VGA, and the only widescreen mode it offered was higher resolution than the display (which did work, but not pixel perfect).

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) explains how to set other modes in X that are not recognized automatically.

PS: A digitally connected monitor (DVI, HDMI) that is not natively the resolution in /etc/usplash.conf may halt boot unless you remove splash as a boot parameter or fix /etc/usplash.conf.  If that is an issue, recovery grub entries should still boot to the console.

---

