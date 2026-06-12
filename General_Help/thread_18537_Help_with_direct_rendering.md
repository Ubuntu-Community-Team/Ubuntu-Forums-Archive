---
title: "Help with direct rendering"
date: 2005-03-07
forum: General Help
---

### Post by Campitor on 2005-03-07
I have had problems setting my direct rendering on Ubuntu.  I previously had FC2 and direct rendering was on.  I wouldnt mind, but I need to install a program that uses direct rendering in order to render 2D plots.  Here's some output from the logs:

eric@Campitor:~ $ cat /var/log/XFree86.0.log |grep rendering
(--) MGA(0): Direct rendering disabled

eric@Campitor:~ $ glxinfo|grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

eric@Campitor:~ $ lspci |grep VGA
0000:00:0b.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2164W [Millennium II]

I know my video card ain't that great...but by looking at the forums it looks like it's supported by UBUNTU and I just need to tweak with some config files to get rendering activated.  I'm fairly new to linux and would appreciate some help (do not assume I speak linux to well), or a confirmation that I won't get DRI working unless I upgrade to a better VGA card.

Thanks

Campitor.

---

