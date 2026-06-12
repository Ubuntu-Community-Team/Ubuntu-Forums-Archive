---
title: "Install the OpenChrome drivers, Dapper"
date: 2006-05-13
forum: General Help
---

### Post by Prism on 2006-05-13
Hi there,

I have a VIA K8M800 video card, and I have some problems playing video. I decided to install the OpenChrome drivers, hoping I'll get better results.

Anyway, I followed the steps from here: [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code) (I have xorg 7.0), compiled the openchrome drivers and the libdrm, but when I tried to execute  [FONT="Courier New"]make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via[/FONT], I got this error message: [FONT="Courier New"]make -C /lib/modules/2.6.15-22-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules[/FONT]

How can I solve the problem? Did I miss something?

---

