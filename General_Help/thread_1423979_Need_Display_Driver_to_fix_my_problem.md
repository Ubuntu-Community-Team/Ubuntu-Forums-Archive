---
title: "Need Display Driver to fix my problem"
date: 2010-03-07
forum: General Help
---

### Post by fasterfish on 2010-03-07
Hi I am new with ubuntu. My video card is a CyberbladeXP by trident with 16 Mb Video. And my laptop is a Toshiba satellite pro 4600. The Screen only shows in 800x600 and I need it into a higher resoulotion to fit my laptop screen. I have went to display preferences and I can not go any higher then that. Can somebody please post a driver to fix my problem, and I might need help installing it.

---

### Post by patchwork on 2010-03-07
Your driver can be downloaded using
```
sudo apt-get install xserver-xorg-video-trident
```...but it's probably already downloaded and it won't solve your problem by itself.  You'll probably need to edit your /etc/X11/xorg.conf to get the desired resolution.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6718464](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6718464)   
# Look at posts 8,9-will link to this:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6718464](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6718464)

---

### Post by Keith1212 on 2010-03-07
> **fasterfish said:**
> Hi I am new with ubuntu. My video card is a CyberbladeXP by trident with 16 Mb Video. And my laptop is a Toshiba satellite pro 4600. The Screen only shows in 800x600 and I need it into a higher resolution to fit my laptop screen. I have went to display preferences and I can not go any higher then that. Can somebody please post a driver to fix my problem, and I might need help installing it.

Hi i had this same problem. Look in you "/usr/lib/xorg/modules/drivers" folder for the file trident_drv.so. I have it in mine so its probably default. So what you need to do is open this file "/etc/x11/xorg.conf". to do this open a terminal and type "sudo gedit /etc/x11/xorg.conf". 

It will look close to this.
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Change the "vesa" to say "trident". and file>save. Reboot all should be well after u select your new resolution.

---

### Post by fasterfish on 2010-03-08
> **Keith1212 said:**
> Hi i had this same problem. Look in you "/usr/lib/xorg/modules/drivers" folder for the file trident_drv.so. I have it in mine so its probably default. So what you need to do is open this file "/etc/x11/xorg.conf". to do this open a terminal and type "sudo gedit /etc/x11/xorg.conf". 

It will look close to this.
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Change the "vesa" to say "trident". and file>save. Reboot all should be well after u select your new resolution.

When I typed in the code in the termanal the thing popped up and it was blank. So I copyed your driver code and changed vesa to trident into it and saved. Then it said can not find xorg.conf.

---

### Post by patchwork on 2010-03-08
> I have it in mine so its probably default. So what you need to do is open this file "**/etc/x11/xorg.conf**". to do this open a terminal and type "sudo gedit /etc/x11/xorg.conf".

The path is /etc/X11/xorg.conf (case-sensitive)

---

### Post by realzippy on 2010-03-08
[B]sudo gedit /etc/[COLOR="Red"]x[/COLOR]11/xorg.conf
[/B]
is mistyped.It had to be:

**sudo gedit /etc/X11/xorg.conf**

---

### Post by fasterfish on 2010-03-08
I typed it in

it is still blank

Then I coped the stuff and changed vesa to trident and saved and this what happend

---

### Post by patchwork on 2010-03-08
Click "Save As..." and change the path....it is trying to save to the wrong path.

---

