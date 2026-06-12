---
title: "For nvidia user, if you got a slow resize window prob."
date: 2009-07-24
forum: General Help
---

### Post by schar on 2009-07-24
with Installed driver:
ii  nvidia-180-kernel-source                   180.44-0ubuntu1                                  NVIDIA binary kernel module source
ii  nvidia-180-libvdpau                        180.44-0ubuntu1                                  Video Decode and Presentation API for Unix
ii  nvidia-180-modaliases                      180.44-0ubuntu1                                  Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-glx-180                             180.44-0ubuntu1                                  NVIDIA binary Xorg driver

with these lines in /etc/X11/xorg.conf:
...
Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection
...

please change to:
Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "dri"      # <---------------must enable load dri
    Load           "glx"
EndSection

or the window resizing will got a 1-2 second delay on rendering.

tested also on linux-mint 7 (ubuntu 9.04) and 8.10.

---

### Post by UranUtan on 2009-07-25
Internet searches about Xorg and DRI didn't find anything useful. May be you can help?

I have the nVidia GeForce 9300 chip and even the nVidia X Server settings utility didn't generate that "load dri" line.

What is DRI and why is it not enabled by default?


Thanks in advance for any clarification.

---

### Post by lekksi on 2009-07-30
> **UranUtan said:**
> Internet searches about Xorg and DRI didn't find anything useful. May be you can help?

What is DRI and why is it not enabled by default?


I found [this link]("http://dri.freedesktop.org/wiki/FrontPage"). I hope it answers your questions.

---

