---
title: "Change boot up screen to the default kde air wallpaper in 9.10"
date: 2009-12-15
forum: General Help
---

### Post by connel on 2009-12-15
All i want is the black background in the usplash/xsplash theme (i actually dont know what kubuntu 9.10 uses) to be the air wallpaper that is default  in kubuntu 9.10. That way the u/xsplash screen, kde splash screen and my wallpaper will all be the same giving me a seamless boot :)

does anyone know if this is possible? :)

---

### Post by Wardje on 2009-12-15
```
/usr/share/images/xsplash
```
is the folder that holds the background for the xsplash, I know changing things here works for regular Ubuntu, if anyone can confirm this is the same for Kubuntu?


Either way, if it does:
the files contained in this folder seem pretty self explanatory to me, replace the bg_* files with the background of your choice. Be sure to pay attention to the resolution and such.
Also, as always when changing stuff, be sure to make a backup of the files in that folder :)

---

### Post by connel on 2009-12-15
ok thanks for the reply!! :D

hmmmmmmmmmmmmm /usr/share/images/xsplash doesnt seem to exist on my install. Either Kubuntu puts them in a different place or it uses usplash. Either way could someone help me do this in kubuntu and not ubuntu please?

---

### Post by darude on 2009-12-26
bump, op is right there is no such directory in Kubuntu Karmic.

However, I have found the wallpaper here:
/usr/share/wallpapers/Air/contents/images

But just replacing the file doesn't do anything to the login wallpaper

---

### Post by darude on 2009-12-26
Found it:

Login wallpaper:
/usr/share/kde4/apps/kdm/themes/oxygen-air/1280x800.jpg

Splash Screen wallpaper:
/usr/share/kde4/apps/ksplash/Themes/Default/1280x1024/background.png

---

### Post by connel on 2009-12-26
hey, thanks for your help darude but i was actually looking to change the background of my xsplash or usplash not the KDM login manager's background as i login automaticaly anyway.


BUMP - Does any one out there no if this is possible? if so what file do i have to change to change my Kubuntu usplash/xsplash black background to the default kde air wallpaper?

thanks x

---

### Post by connel on 2010-01-01
BUMP.
does any one have any idea how to do this please?

---

