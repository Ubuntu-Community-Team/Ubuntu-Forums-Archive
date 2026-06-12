---
title: "Don't have nor can find application"
date: 2009-08-19
forum: General Help
---

### Post by Silvernail on 2009-08-19
I need a full screen slide show. This is what I have but can not find. Any suggestion I can download?

Thanks
Dave


dave@gadabout:~$ cd /media/KINGSTON

dave@gadabout:/media/KINGSTON$ apropos slide
QSlider (3qt)        - Vertical or horizontal slider
**glslideshow (6x)     - slideshow of images using smooth zooming and fades**
inkview (1)          - slideshow program which uses SVG files
makeslides (1)       - (unknown subject)
qslider (3qt)        - Vertical or horizontal slider
slidescreen (6x)     - permute the screen image like an 8-puzzle


dave@gadabout:/media/KINGSTON$ glslideshow
bash: glslideshow: command not found

dave@gadabout:/media/KINGSTON$ apropos glslideshow
glslideshow (6x)     - slideshow of images using smooth zooming and fades

dave@gadabout:/media/KINGSTON$ locate glslideshow
/usr/lib/xscreensaver/glslideshow
/usr/share/applications/screensavers/glslideshow.desktop
/usr/share/man/man6/glslideshow.6x.gz
/usr/share/xscreensaver/config/glslideshow.xml

dave@gadabout:/media/KINGSTON$ sudo apt-get install glslideshow
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glslideshow

dave@gadabout:/media/KINGSTON$ man glslideshow
I have the manual.

---

### Post by mcduck on 2009-08-19
"glslideshow" is actually a screensaver, if I remember right... ;)

Anyway, at least both Gthumb (the default image viewer in Gnome) and F-Spot can do full-screen slideshows. So can pretty much any image viewer you can find.

edit: what comes to your commands above, "apropos" finds glslideshow because it's already installed on your system. Apropos only searches what you already have installed. "apt-get" can't find it because there is no such package (it comes bundled together with several other screensaver), and trying to run "glslideshow" fails because it's not a standalone program. :)

---

### Post by PGScooter on 2009-08-19
I think mcduck is right.

If you don't have mcduck's memory, the way I use to find out that gslideshow is a screensaver is:
```
dpkg-query -S glslideshow
xscreensaver-gl: /usr/share/xscreensaver/config/glslideshow.xml
xscreensaver-gl: /usr/share/applications/screensavers/glslideshow.desktop
xscreensaver-gl: /usr/share/man/man6/glslideshow.6x.gz
xscreensaver-gl: /usr/lib/xscreensaver/glslideshow

```
and then if you want further info, do:
```
apt-cache show xscreensaver-gl
```

---

### Post by Silvernail on 2009-08-19
Thanks guys for the feed back.
I could not find a loop key for 'gwenview'.
I could not find a change dir or a loop key of 'fspot'.

Ya'll triggered the memory that I had used 'feh' in a shell script for a last christmas party.

That works.
Thanks again
Dave

---

