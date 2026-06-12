---
title: "Login Window Very small font"
date: 2009-08-04
forum: General Help
---

### Post by Dougie085 on 2009-08-04
I'm not sure whats going on here but when I logout all the text on the login window is so small you can't read it. It's normal size when logged in and using Ubuntu but when I logout its very very small. Any ideas?

---

### Post by running_rabbit07 on 2009-08-04
Try changing you theme in System>Administration>Login Window. This may help.

---

### Post by Zorael on 2009-08-04
In some cases you may need to explicitly define what DPI it should use. For this you'd need to open up **/etc/gdm/gdm.conf** in a text editor with superuser permissions, such as by running '**gksu gedit /etc/gdm/gdm.conf**' in a run box (alt+f2).

Search for the part that looks like this, and add the highlighted (highlit?) text.
```
[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-nolisten tcp **[COLOR="Lime"]-dpi 96[/COLOR]**
ServerCmd=/usr/bin/X -br
```
There may be comments inbetween those lines (extra lines prepended with hashmarks **#**), so your file may look a bit different. Still, "ServerArgsLocal" is the line you want to modify to add **[COLOR="Lime"]-dpi 96[/COLOR]** to.

---

### Post by Dougie085 on 2009-08-04
I can't find ServerArgsLocal anywhere in my gdm.conf file. I looked all through the file and I also tried searching.

I did try changing the theme a couple times before I posted.

---

### Post by Dougie085 on 2009-08-04
I figured it out, you have to change it in the xorg.conf file. Looks much better now :)

---

### Post by Zorael on 2009-08-04
The gdm.conf example was pulled from a google result - perhaps they look different in more recent releases. I only have a copy of kdmrc to properly paste from.

---

