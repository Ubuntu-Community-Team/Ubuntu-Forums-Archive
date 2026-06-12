---
title: "Boot splash"
date: 2011-02-22
forum: General Help
---

### Post by NikoC on 2011-02-22
Ubuntu 10.10 is working flawlessly on my laptop, I even managed to fix the boot splash image and resolution, yet I still have some minor annoyances:

- when booting I always get a blinking cursor before the plymouth splash screen appears: is there a way to get rid off that and immediately show the splash screen?

- on shutdown: before showing the splash screen, I get a black screen with some terminal output. Again, is it possible to immediately show the splash shutdown image?

Thanks.

---

### Post by NikoC on 2011-02-23
*bump*

---

### Post by stinkeye on 2011-02-23
This fixed the issue on my nvidia card.
Don't know if it's nvidia specific.

Create this file.
```
gksudo gedit /etc/initramfs-tools/conf.d/splash
```
and add this option 
```
FRAMEBUFFER=y
```
save the file.


Then
```
sudo update-initramfs -u
```

---

### Post by NikoC on 2011-02-24
> **stinkeye said:**
> This fixed the issue on my nvidia card.
Don't know if it's nvidia specific.

Create this file.
```
gksudo gedit /etc/initramfs-tools/conf.d/splash
```
and add this option 
```
FRAMEBUFFER=y
```
save the file.


Then
```
sudo update-initramfs -u
```

For me that fixed the issue of not having a bootsplash at all a couple of months ago, but not the blinking cursor and shutdown annoyance...

Thanks for the reply though.

---

### Post by stinkeye on 2011-02-25
Done a few fixes. May have mixed them up.
The only other changes I made was adding 
**GRUB_GFXPAYLOAD_LINUX**
and changing
**GRUB_GFXMODE**
to both use my monitors native resolution.

eg I added these two lines to **/etc/default/grub**
```
GRUB_GFXMODE="[COLOR="Magenta"]1680x1050[/COLOR]"
GRUB_GFXPAYLOAD_LINUX="[COLOR="#ff00ff"]1680x1050[/COLOR]"
```
[COLOR="#ff00ff"]Your monitors native resolution.[/COLOR]

..and then run 
```
sudo update-grub
```

---

### Post by NikoC on 2011-02-25
> **stinkeye said:**
> Done a few fixes. May have mixed them up.
The only other changes I made was adding 
**GRUB_GFXPAYLOAD_LINUX**
and changing
**GRUB_GFXMODE**
to both use my monitors native resolution.

eg I added these two lines to **/etc/default/grub**
```
GRUB_GFXMODE="[COLOR="Magenta"]1680x1050[/COLOR]"
GRUB_GFXPAYLOAD_LINUX="[COLOR="#ff00ff"]1680x1050[/COLOR]"
```
[COLOR="#ff00ff"]Your monitors native resolution.[/COLOR]

..and then run 
```
sudo update-grub
```

Tried that as well, but still the same annoyances :(
Using ATI video card btw.

---

