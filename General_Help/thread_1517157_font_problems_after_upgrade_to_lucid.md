---
title: "font problems after upgrade to lucid"
date: 2010-06-24
forum: General Help
---

### Post by karim.rahim on 2010-06-24
After upgrading to Lucid I get the following warnings which I did not have before:

Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct

These occur when I start emacs and xpdf. On searching I see people are adding font paths to their xorg.conf file but on looking at mine there is no longer a font section.

Also I have few directories fonts/X11 
/usr/share/fonts/X11$ ls
misc/  util/

I'm assuming the above folders and xorg.conf file are correct. 

I wondering if anyone else is having this issue.

---

### Post by ajgreeny on 2010-06-24
I have never upgraded, so don't hasve any comments on whether or not that is behind your problem, but try running ```
sudo fc-cache -f -v
``` in terminal to see if that update affects the way your cache of fonts is used.

---

