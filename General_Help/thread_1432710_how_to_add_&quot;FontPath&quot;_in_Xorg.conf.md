---
title: "how to add &quot;FontPath&quot; in Xorg.conf"
date: 2010-03-18
forum: General Help
---

### Post by laomiao on 2010-03-18
I just installed xemacs-21 on Ubuntu 8.04, and I'd like to add some truetype fonts for emacs, some online articles told me I should add lines like below to make emacs find new fonts:

Section "Files"
      FontPath     "/path/to/new-fonts"
EndSection

Section "Modules"
      Load      "freetype"
EndSection

I added above lines to /etc/X11/xorg.conf and restarted Ubuntu, and to my disappointment that the X reported some problem and changed to ugly low resolution version. after I deleted above lines X is back to normal.

So what did I do wrong? I don't know much about xorg.conf, but I did play with XFree86Config a long time ago, those lines didn't cause any problem...

thanks for any input.

---

