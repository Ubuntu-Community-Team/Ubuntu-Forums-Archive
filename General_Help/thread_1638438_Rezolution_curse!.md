---
title: "Rezolution curse!"
date: 2010-12-05
forum: General Help
---

### Post by zmolix on 2010-12-05
After nobody was able to help me her [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1616132](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1616132)
I switched to my onboard Video Card **CN896/VN896/P4M900 [Chrome 9 HC]** .
Here is a bigger problem, compiz dosen't work, hd videos, some flash.

P.S. 1 I have formated HDD and installed again Ubuntu 10.10 
P.S. 2 Ubuntu automatic installed the xserver-xorg-video-openchrome, 
P.S. 3 The /etc/X11/xorg.conf is empty ! 

Please some help !

---

### Post by davidmohammed on 2010-12-05
I would recommend you stick to linux friendly graphics - nvidia and intel.

You can pick up a cheap nvidia card for less than £20 on ebay.

I may be wrong, but I seem to remember reading somewhere that your ancient graphics card isnt supported for 3D graphics etc.

---

### Post by zmolix on 2010-12-05
> **davidmohammed said:**
> I would recommend you stick to linux friendly graphics - nvidia and intel.

You can pick up a cheap nvidia card for less than £20 on ebay.

I may be wrong, but I seem to remember reading somewhere that your ancient graphics card isnt supported for 3D graphics etc.

That is a lot for my budget, Romania has an comunist-alcoholic president that cannot handle the economic crisis .. and we are now all affected by this. 

So .. some trick .. on the first post or to this problem ? Please !

---

### Post by davidmohammed on 2010-12-05
look at [this]("https://wiki.ubuntu.com/X/Config/Resolution") link (search for adding undetected resolution) for your ATI card.

---

### Post by zmolix on 2010-12-05
> **davidmohammed said:**
> look at [this]("https://wiki.ubuntu.com/X/Config/Resolution") link (search for adding undetected resolution) for your ATI card.
 
I've tried that.. all them .. before.. it's useless.. xorg.conf it's empty, but what's frustrating it's that in Ubuntu 8.0 works.

---

### Post by davidmohammed on 2010-12-05
you normally have to turn off KMS first before you try this.

try booting with nomodeset as your grub option...

when booting press shift to display your grub kernels.  Press e to edit.

find the line ending 'quiet splash --'

change the line to

nomodeset quiet splash --

---

