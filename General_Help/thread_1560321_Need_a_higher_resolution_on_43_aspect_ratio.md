---
title: "Need a higher resolution on 4:3 aspect ratio"
date: 2010-08-24
forum: General Help
---

### Post by Magma828 on 2010-08-24
My monitor has an aspect ratio of 4:3, and anything else gets squished/stretched, or doesn't show at all.

The problem is that the max resolution I can find on ubuntu for 4:3 is 800x600, which is horrible :(

Is there somewhere I can get extra resolutions from? I'm using 10.04 LTS Desktop Edition, and it's a completely fresh installation.

---

### Post by Vaphell on 2010-08-24
do you have gfx drivers installed?

---

### Post by Magma828 on 2010-08-24
Not that I know of. I installed ubuntu literally half an hour ago, and haven't installed anything extra since. The gfx is onboard, if that makes a difference. I thought it might be something to do with proprietary drivers, but nothing came up when I checked System -> Admin -> Hardware Drivers.

---

### Post by Vaphell on 2010-08-24
in terminal run lspci, look for VGA in the output

---

### Post by Magma828 on 2010-08-24
> **Vaphell said:**
> in terminal run lspci, look for VGA in the output

Okay, I got this: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

Does this need a driver?

---

### Post by Vaphell on 2010-08-24
do you have xserver-xorg-video-sis package installed? check your System->Administration->System Logs (or whatever it's called), look into Xorg.log if sis module is being loaded. If that's the case, you will probably have to get your hands dirty and configure video modes manually in xorg.conf file

---

### Post by Magma828 on 2010-08-24
> **Vaphell said:**
> do you have xserver-xorg-video-sis package installed? check your System->Administration->System Logs (or whatever it's called), look into Xorg.log if sis module is being loaded. If that's the case, you will probably have to get your hands dirty and configure video modes manually in xorg.conf file

Yeah xserver-xorg-video-sis is installed, and it looks like SIS is being loaded in xorg.log.

Where can I find the xorg.conf file?

---

### Post by Vaphell on 2010-08-24
by default there is none because system tries to autoconfigure things but when it fails you can override its settings with that file. It's default location is /etc/X11

I am not a specialist of xorg.conf tweaking, google a bit 'xorg.conf sis', maybe you'll get lucky.

---

### Post by Magma828 on 2010-08-25
That looks nasty.. can I use xrandr, or do I have to use xorg.conf?

I tried using xrandr with 1024x768, which I know my monitor supports because I've used it with this resolution on my other computer that also runs the same version of ubuntu, but it didn't work.

I tried this:
```

cvt 1024 768
- Copied above output into below command
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode default "1024x768_60.00"
xrandr --output default --mode "1024x768_60.00"

```
And at the end I get this error: xrandr: Configure crtc 0 failed

If xrandr didn't work, does this mean editing xorg.conf wont work either?

---

### Post by LowSky on 2010-08-25
can you post your /etc/X11/xorg.conf file?

---

### Post by Magma828 on 2010-08-25
> **LowSky said:**
> can you post your /etc/X11/xorg.conf file?

It doesn't exist =/

---

### Post by Grenage on 2010-08-25
I'd recommend just using an xorg.conf.  I have a guide [here]("http://www.grenage.com/xorg.html"), and there are many others about.

Failing that, as LowSky said, post what you have here and we can guide you.

---

