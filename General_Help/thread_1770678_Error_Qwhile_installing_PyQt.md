---
title: "Error Qwhile installing PyQt"
date: 2011-05-29
forum: General Help
---

### Post by chegini on 2011-05-29
[SIZE=2]Hi friends,[/SIZE]

I[SIZE=2]'m a newbie in Ubuntu and I'm trying to install PyQt-x11 on my Ubuntu 10.10 64bit. While trying to make, I get the following error:

-L/usr/lib -L/usr/X11R6/lib -lQtHelp -lQtGui -lQtCore -lXext -lX11 -lm -lpthread
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
make[1]: *** [QtHelp.so] Error 1
make[1]: Leaving directory `/Software/academic/PyQt-x11-gpl-4.8.4/QtHelp'
make: *** [all] Error 2[/SIZE]

[SIZE=2]I already have the [COLOR=#000000][FONT=Arial] libx11-dev installed[/FONT][/COLOR] but I don't have a X11R6 directory in my usr file, could that be the problem?

I have also got these files in my usr/lib64 and usr/lib and usr/lib32
libXext.so.6.4.0
libXext.so.6
libXext.so[/SIZE]

If anyone could help me it would be most appreciated. I've been stuck for hours and searched all the webs too!

---

