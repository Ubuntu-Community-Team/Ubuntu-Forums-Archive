---
title: "Asus laptop brightness problem"
date: 2009-11-01
forum: General Help
---

### Post by lungan on 2009-11-01
Hi!

Since i've upgraded to the new version, now my light sensor now controls my brightness, my FN keys dont work to adjust the brightness, I have to keep a strong light in front of the light sensor, if I don't the screen becomes very dark.

---

### Post by Nailox on 2009-12-23
KARMIC user

A) Open Terminal (Menu->Accessories), and type the following:
 	Code:
 	sudo gedit brightness 
B) Now paste the following in the Terminal window:
 	Code:
 	#!/bin/sh
echo -n 0 > /sys/devices/platform/asus_laptop/ls_switch 
C) Save your file. 

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
 	Code:
 	sudo mv brightness /etc/init.d
sudo chmod 755 /etc/init.d/brightness
sudo update-rc.d brightness defaults 90 
E) Reboot, and you will have regained control of your brightness level.

thanks to ricaxe
[]("http://ubuntuforums.org/showthread.php?t=926176&highlight=ambient+light+sensor")

---

### Post by wayners on 2010-03-28
[B]I have an Evesham Z7100 laptop. Made by asus. Had a very dark screen. When i put light sorce on sensor (Top of screen) the screen brightened. Followed this fix then right clicked on bottom bar and added panel. Add brightness applet and slider works to adjust brightness even after reboot.
Taken from this web site
[http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)

[/B]



**1. Screen Brightness**
 The ambient light sensor is the cause of the dim screen, we&#8217;ll have to turn it off. To fix this we will have to create a shell script that will be run on boot up that will turn of the ambient light sensor.
 **A)** Open Terminal (Menu->Accessories), and type the following:
[COLOR=#0000ff]sudo nano brightness[/COLOR]
 **B)** Now paste the following in the Terminal window:
[COLOR=#0000ff]#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch
[/COLOR]  [B]Press enter
C)[/B] Hit *Ctrl-O* to save and then *Ctrl-X* to exit. If you see cancel or cancel and exit you have done something wrong.
 **D) **Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
[COLOR=#0000ff]sudo mv brightness /etc/init.d[/COLOR]
and then
[COLOR=#0000ff]sudo chmod 755 /etc/init.d/brightness[/COLOR]
and then
[COLOR=#0000ff]sudo update-rc.d brightness defaults 90[/COLOR]
 **E)** Reboot, and you will have regained control of your brightness level.

---

