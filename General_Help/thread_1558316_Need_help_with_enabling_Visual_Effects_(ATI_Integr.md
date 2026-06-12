---
title: "Need help with enabling Visual Effects (ATI Integrated Graphics)"
date: 2010-08-22
forum: General Help
---

### Post by irok30278 on 2010-08-22
Hello, I'd like to start off by saying that I'm very new to Ubuntu and to this forum so forgive me if I sound stupid.  I would like to know if there is any way to enable Visual Effects (System->Preferences->Appearance) without having a video card driver installed.  I am running Ubuntu 10.04 as a guest OS using VirtualBox with VBOX Additions installed.  I am trying to get this to work without a video driver because all of the drivers I have tried have failed.  I tried ATI's proprietary Catalyst drivers and got the "No supported adapters detected" error, which I assume means my HD 3200 integrated graphics is not supported by ATI anymore.  I have also tried the generic drivers (fglrx) with absolutely no luck whatsoever. When I go into my hardware drivers it reads "No proprietary drivers are in use on this system".  If somebody could point me in the right direction on how to get ATI drivers to work or how to make the Visual Effects work without any drivers at all, it would be greatly appreciated.  This seems like a very helpful forum so I figured I'd give it a shot.  Thanks in advance.

---

### Post by sikander3786 on 2010-08-22
Virtual Box does not support 3D. It has its own graphics adapter installed rather than using the actual hardware. No way getting the 3D effects inside the VB.

Make a fresh dediacted Ubuntu install on your HD if you want to see those amazing effects.

Regards.

---

### Post by earthpigg on 2010-08-22
in VirtualBox, select the machine and go to settings.

from there, display -> enable 3d and 2d acceleration

i think there are some wonky things you have to do to make it work. i don't remember what they are, though. virtualbox's documentation is outstanding, so i've never had to remember :P


> Virtual Box does not support 3D. It has its own graphics adapter installed rather than using the actual hardware. No way getting the 3D effects inside the VB.

that statement hasn't been true for a year or two.

---

### Post by sikander3786 on 2010-08-22
> **earthpigg said:**
> in VirtualBox, select the machine and go to settings.

from there, display -> enable 3d and 2d acceleration

i think there are some wonky things you have to do to make it work. i don't remember what they are, though. virtualbox's documentation is outstanding, so i've never had to remember :P




that statement hasn't been true for a year or two.

Are you saying that it is possible now? The last time I checked VB, the 3D effects were very very much poor. And I am not sure if all the compiz effects can be enabled in VB even nowadays.

---

### Post by earthpigg on 2010-08-22
> **sikander3786 said:**
> And I am not sure if all the compiz effects can be enabled in VB even nowadays.

i believe i distinctly recall spinning some cubes around in vbox. as i recall, setting it up was a bit wonky and i had to read through some of virtualbox's documentation.

---

### Post by irok30278 on 2010-08-22
Well, thanks for the help.  I couldn't get it to work in VBox so I just decided to fully install Ubuntu on a separate drive partition and everything works like it's supposed to.

---

