---
title: "Adobe Photoshop CS4 Install"
date: 2010-09-15
forum: General Help
---

### Post by lostprophetpunk on 2010-09-15
I have recently converted to Ubuntu, so I must mention now I am new to Ubuntu.

The Ubuntu version I am running is 10.04

I was looking for ways to install Adobe Photoshop CS5, but when I try to run the Setup.exe with WINE, it runs the installing setup, but then after it loads the window closes and it doesn't do anything from that.

Is there any way to fix this at all? As I am starting to miss Photoshop.

P.S. I know there is an alternative program such as GIMP, but it takes forever to do something in GIMP which it takes like 1 minute in Photoshop to do.

If there is not a fix for this...is there a program that is like Photoshop, but not like GIMP?

Thanks in advance.

---

### Post by TwelveGauge on 2010-09-15
how have you configured wine? 
I'd suggest removing wine with synaptic then reinstall it

```
sudo apt-get install wine
sudo apt-get upgrade
winecfg
#configure wine
wine /path/to/photoshop/whatever.exe
```make sure you deselect "run in terminal"

additionally, photoshop may require you to run it from a specific location in which case you'll have to do this (if you still have trouble)

```
sh -c cd /home/theUser/.wine/drive_c/Program Files/appdir/; wine /home/theUser/.wine/drive_c/Program Files/Appdir/game.exe
```Replace theUser with your name and replace appdir with the application's directory.

---

### Post by raafaell on 2010-09-15
Try following this [guide]("http://www.makeuseof.com/tag/idiots-guide-installing-photoshop-cs5-ubuntu-1004/") and see what happens..

---

### Post by TwelveGauge on 2010-09-15
I actually tried that on my computer for illustrator (yes, I know it's different) and it worked sort of...it kept doing screwy things with the fonts and things. So in the end I just uninstalled everything and ran what i put up there and it worked =/ 

It's a good guide though and it's possible that my computer is just nuts.

---

### Post by lostprophetpunk on 2010-09-15
> **raafaell said:**
> Try following this [guide]("http://www.makeuseof.com/tag/idiots-guide-installing-photoshop-cs5-ubuntu-1004/") and see what happens..
I have followed this guide, but when I click on the setup.exe bit it gives me an error.

---

### Post by TwelveGauge on 2010-09-15
what error?

---

### Post by lostprophetpunk on 2010-09-16
> **TwelveGauge said:**
> what error?
Sorry, I was getting mixed up with another version of Photoshop I was trying to install.

I run the Setup.exe for CS5 and the adobe installer loads, but once it finishes loading...it disappears and then nothing else happens, such as the actual setup would ideally run after the adobe setup has finished loading...but nothing happens...no error or anything.

I did follow that guide raafaell posted, but the above happened.

---

