---
title: "Changing the resolution of a remote headless Ubuntu server?"
date: 2012-06-07
forum: General Help
---

### Post by Mesopotamia on 2012-06-07
Hi everyone,

I'm using the built-in VNC server on the new 12.04 OS on my remote server. There is no monitor connected to it.

When I VNC to it, the resolution seems to be 800x600 but I need 1920x1200.

Can anybody shed a light of this can be achieved?

Thanks

---

### Post by zero2xiii on 2012-06-07
Hay,

Not sure about what VNC server you are using and if that might be restricting your resolution, but check your xorg config file found at: /etc/xorg.conf. Note that you location may be different, check the man pages for xorg for the different locations.

Then look for the line containing the current resolution and change that to the desired resolution.

I use the proprietry nvidia drivers on my machine so things work a bit different (my xorg.config is empty). But this should work, or maybe try altering the config files of the VNC server itself.

Cherz

---

