---
title: "Night mode color temperature (F.lux or Redshift) for KDE ?"
date: 2011-02-28
forum: General Help
---

### Post by scotty64 on 2011-02-28
I am looking for an application that allows me to put the Desktop in "Night Mode" by reducing brightness and shifting the colortemperature to the red side. I am aware of two applications that do this automatically (F.lux and Redshift), but both are GNOME applications - I could not get them run under KDE.
Any similar applications for KDE ?

---

### Post by jakupl on 2011-02-28
[http://www.tux-crazy.com/2011/01/protect-your-vision-from-computer.html](http://www.tux-crazy.com/2011/01/protect-your-vision-from-computer.html)

---

### Post by scotty64 on 2011-02-28
> **jakupl said:**
> [http://www.tux-crazy.com/2011/01/protect-your-vision-from-computer.html](http://www.tux-crazy.com/2011/01/protect-your-vision-from-computer.html)

Tried it already. The KDE showstopper is that it depends on gnome-settings-daemon running: [https://github.com/Kilian/f.lux-indicator-applet/issues#issue/3](https://github.com/Kilian/f.lux-indicator-applet/issues#issue/3)

---

### Post by jakupl on 2011-02-28
> **scotty64 said:**
> Tried it already. The KDE showstopper is that it depends on gnome-settings-daemon running: [https://github.com/Kilian/f.lux-indicator-applet/issues#issue/3](https://github.com/Kilian/f.lux-indicator-applet/issues#issue/3)

It might be possible to hack out a solution involving anacron and some weird program, but i would simply install gnome-settings-deamon on kubuntu. That should only be a problem if you have limited hard disk space, because it will probably pull in all the gnome libraries.

---

### Post by Zorael on 2011-03-01
What does this do? Does it lower brightness or change color balances?

As a poor-man's solution, you can probably emulate this with xrandr and xgamma if nothing else, unless you have a Nvidia card and you run the proprietary driver. I lower the brightness on my netbook at night that way.
```
$ xrandr --output LVDS1 --brightness 0.5
```

---

### Post by anchorschmidt on 2011-03-07
Hello, I'm the guy who wrote the article ([http://www.tux-crazy.com/2011/01/protect-your-vision-from-computer.html](http://www.tux-crazy.com/2011/01/protect-your-vision-from-computer.html))
I think that it is possible to get xflux running using the instructions that I provided for "Other Linux Distros". I've managed to get it to work on a Debian Squeeze installation.

---

### Post by scotty64 on 2011-03-07
> **anchorschmidt said:**
> Hello, I'm the guy who wrote the article ([http://www.tux-crazy.com/2011/01/protect-your-vision-from-computer.html](http://www.tux-crazy.com/2011/01/protect-your-vision-from-computer.html))
I think that it is possible to get xflux running using the instructions that I provided for "Other Linux Distros". I've managed to get it to work on a Debian Squeeze installation.

Thanks for your help ! Command line xflux works fine under KDE - the only sad thing is that it is not open sourced (yet).

---

### Post by anchorschmidt on 2011-03-17
You're most welcome. Redshift is another program that does the job and I think that it's open-source [http://jonls.dk/redshift/](http://jonls.dk/redshift/)

---

### Post by scotty64 on 2011-03-18
> **anchorschmidt said:**
> You're most welcome. Redshift is another program that does the job and I think that it's open-source [http://jonls.dk/redshift/](http://jonls.dk/redshift/)
I already shifted to Redshift - it is completely opensource and it has more options and a working tray icon that lets you toggle the nightmode.

---

### Post by suda on 2011-05-01
I'm going to make a new post on a similar topic: Redshift.  

Suda

---

