---
title: "No Desktop... on boot up :("
date: 2006-04-14
forum: General Help
---

### Post by Efrain Valles on 2006-04-14
I recently upgraded from Hoary to breezy
This seems pretty simple...
I get no desktop...

after I run a file browser, I get the wallpaper and the icons.. but not on boot up...
:(

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=Efrain Valles]I recently upgraded from Hoary to breezy
This seems pretty simple...
I get no desktop...

after I run a file browser, I get the wallpaper and the icons.. but not on boot up...
:([/QUOTE]
I would recommend a clean install. Even if you dist-upgrade not everything will go right all the time. Try to backup all valueable data and the do a clean install.

---

### Post by Ramses de Norre on 2006-04-14
maybe ```
sudo apt-get install --reinstall nautilus nautilus-data
``` will work.

---

### Post by Efrain Valles on 2006-04-14
Thanks Guys... I'm on it...

Edit:
I am trying to fix this... It is only a glitch... when I start my session it doesn't load Nautilus and the file system. however when I manually start the File Browser the background image and the desktop icons appear...

I tried installing nautilus again but it didn't fix it... 

you know how everytime you log in you have a splash image with 4 icons loadin metacity  panel  nautilus  etc??

well Mine only loads metacity and panel

---

### Post by Efrain Valles on 2006-04-14
I found a way around it... I added Nautilus to the boot up sequence and it worked like a charm... thanks guys...

---

### Post by Ramses de Norre on 2006-04-14
System > preferences > sessions > startup programs tab > add 
for command give nautilus and for order give 40.
That's how it runs on my system automaticaly.

EDIT: too late ;)

---

