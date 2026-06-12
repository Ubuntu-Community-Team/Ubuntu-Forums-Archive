---
title: "Help? Blank screen on boot, 10.04 64bit. Graphics/sound card issue?"
date: 2011-02-19
forum: General Help
---

### Post by lelandnielsen on 2011-02-19
Noob here.  I was trying to configure my graphics and sound cards today, did a reboot as required by one of the configurations, and now I get a blank screen on startup.  

I tried this:
[http://ubuntuforums.org/showthread.php?t=1494430](http://ubuntuforums.org/showthread.php?t=1494430)
... editing GRUB, but no good in either modeset or noapic.

What got me here was adding: 
snd-ice1712 [something something]
to the bottom of /etc/modeset.d/alsa-sound.conf

I have an MAudio Delta1010LT and an PNY nVidia Quadro.  

Help?

---

### Post by lelandnielsen on 2011-02-19
I got back in by deleting "vga=769" in GRUB.  

I found it here:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/578028/comments/9](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/578028/comments/9)

But now what?

---

