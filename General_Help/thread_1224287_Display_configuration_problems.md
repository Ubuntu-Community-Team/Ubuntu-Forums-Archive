---
title: "Display configuration problems"
date: 2009-07-27
forum: General Help
---

### Post by jacklisse on 2009-07-27
I don't know if this is the righ place for this, but here goes:
 
I have a decent computer, AMD 64 4500+ with 2GB of RAM, and an ATI Radeon video card.
I use Ubuntu 8.04, it works fine, until I download the ATI drivers.
everytime I download the drivers the display settings are automaticaly set to the highest and my monitor can't handle it.
So when I restart my computer after installing the ATI drivers my monitor goes off, and I can't change the settings if I can't see the screen.
Is there a way to lock the display settings before installing the drivers, or an easy way to change them using the terminal? (I'm new to ubuntu)

---

### Post by JDShu on 2009-07-27
You can try editing xorg.conf and manually set the display for X, your windows manager.

---

### Post by fvanham on 2009-07-27
this can be done by logging in terminal alt-ctrl-F1 (F1 -> F6 should be terminals)
then you enter te command : ```
sudo nano /etc/X11/xorg.conf
```to exit the editor you press ctrl+X (see bottom => ^X )
then you press Y
and then ENTER

you could, and you sould backup your xorg.conf before you start editing :)
you can do this with a command like: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup1  
```or something like that... and reverse the files to put the backup back...
```
sudo cp /etc/X11/xorg.conf.backup1 /etc/X11/xorg.conf
```To find some xorg.conf examples you can use the internet.
Your favorite search engine should do the trick. I should remind you, that you only should edit the parts that need editing.

maybe pasting the content of xorg.conf here would make it more easy to tell you what to change :)

you could copy the file (that doesn't work for your screen) here :)

---

### Post by ajgreeny on 2009-07-27
If you know exactly the resolution and refresh rates of your monitor you can edit the xorg.conf file to look a bit like this example from my system, which in intrepid detected the monitor wrongly.
```
Section "Device"
    Identifier    "Configured Video Device"
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
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
I've omitted all the text at the top of the file as it will not help your problem, but the working part is shown.  I hope it helps.  By the way I also have an ATI card, but mine is old and uses the OS drivers.

---

### Post by prshah on 2009-07-27
> **jacklisse said:**
> 
everytime I download the drivers the display settings are automaticaly set to the highest and my monitor can't handle it.

I suggest you add/edit the following lines to your /etc/X11/xorg.conf as suitable```
Section "Monitor"
    Identifier    "Configured Monitor"
[color=red]    Option "PreferredMode" "1024x768"[/color]
EndSection


Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
[color=red]    SubSection "Display"
        Modes    "1024x768@60"
    EndSubSection[/color]
EndSection

```

You will have to know the native resolution / refresh rate of your  screen / monitor; don't blindly add these lines. Replace the resolution as you feel suitable.

As previously mentioned, you can drop to a virtual terminal with Ctrl+Alt+F1 (..F6) and use pico or nano to edit the xorg.conf file```
sudo pico /etc/X11/xorg.conf
```, then, after saving and exiting, restart X with ```
sudo /etc/init.d/gdm restart
```

---

