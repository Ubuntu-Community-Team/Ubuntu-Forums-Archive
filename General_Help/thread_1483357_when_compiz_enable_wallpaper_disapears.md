---
title: "when compiz enable wallpaper disapears"
date: 2010-05-14
forum: General Help
---

### Post by elliotn on 2010-05-14
When i enable compiz I lose my wallpaper and i get a back screen with no wallpaper no icons.

But when i do metacity --replace all goes well but have no effecs. Help

---

### Post by ajgreeny on 2010-05-14
I assume you are running your ati card with the default ati/radeon driver installed and assigned at installation of the OS.

Options available are to run without compiz, which you obviously don't want to have to do, to run at a resolution no higher than 1024x768, which is silly if you have a large monitor, or to set /etc/X11/xorg.conf to run x at 16 bit colour, which is what I did in karmic and continue to do in Lucid.

Here is my xorg.conf for you to use as a template
```
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```
Use your own figures for refresh rates and resolution, or leave them out completely as I don't think they are needed.  I hope this helps you

---

### Post by elliotn on 2010-05-15
now am lost, u want me to copy the above .conf file or?

Btw if it help previously I was using an old samsung monitor all used to work very well, last week i changed the monitor and put a new 19" lg flatron... Thats were all hell began.
My gfx card is ati 7000 series

---

### Post by elliotn on 2010-05-15
bumping hoping to getting a solutioning of the probleming

bump

---

### Post by ajgreeny on 2010-05-15
Try changing things as I said in my first post as your problem must, I think be related to the now higher resolution of the large screen.

First use the command ```
gksudo gedit /etc/X11/xorg.conf
```which will either open up your current xorg.conf file or make a new empty one.  Copy the contents I showed of my file to that empty(?) file, but add your screen resolution in the same pattern as I show in place of my figures.  You can also remove the HorizSync and VertRefresh lines as they are for my monitor, and may be wrong for yours; they should not really be needed anyway.  Save that file, which will be possible as you opened it with the "gksudo gedit" command.

Now simply logout and in again to restart x and you should find that with 16 bit colour you can get compiz running again.

---

### Post by elliotn on 2010-05-17
that worked perfectly

---

### Post by elliotn on 2010-05-17
k gues its solved

---

