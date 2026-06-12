---
title: "Ooops I broke my Ubuntu 11.10 login screen!?!?"
date: 2011-10-30
forum: General Help
---

### Post by Hulmemanitarian on 2011-10-30
Would appreciate ANY help with my problem? I've recently installed 11.10 and decided to change the logon screen via gksu gedit /etc/lightdm/unity-greeter.conf. That went OK, until I mistakenly removed the entire greeter line? Now my beautiful ubuntu install just displays the purple loading screen? I've reinstalled lightdm via the terminal after removing it, but I just need to put the default login back where it belongs. PLEASE HELP!?!?:confused:

---

### Post by coffeecat on 2011-10-30
I don't know whether this will help, but this is the contents of a default /etc/lightdm/unity-greeter.conf.

```
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# logo = Logo file to use
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
background=/usr/share/backgrounds/warty-final-ubuntu.png
logo=/usr/share/unity-greeter/logo.png
theme-name=Ambiance
icon-theme-name=ubuntu-mono-dark
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=hintslight
xft-rgba=rgb
```

If your /etc/lightdm/unity-greeter.conf is the problem, you could restore it by booting into recovery mode and editing it with nano (fiddly), or booting with a live CD, mounting your Ubuntu partition and using a gksu gedit text editor.

---

### Post by Hulmemanitarian on 2011-10-30
> **coffeecat said:**
> I don't know whether this will help, but this is the contents of a default /etc/lightdm/unity-greeter.conf.

```
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# logo = Logo file to use
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
background=/usr/share/backgrounds/warty-final-ubuntu.png
logo=/usr/share/unity-greeter/logo.png
theme-name=Ambiance
icon-theme-name=ubuntu-mono-dark
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=hintslight
xft-rgba=rgb
```

If your /etc/lightdm/unity-greeter.conf is the problem, you could restore it by booting into recovery mode and editing it with nano (fiddly), or booting with a live CD, mounting your Ubuntu partition and using a gksu gedit text editor.

Thanks for the help CoffeeCat. Don't suppose there are any live CD/gksu with gedit text editor 101s? I have the 11.04 live CD. *wounded*

---

### Post by coffeecat on 2011-10-30
The live 11.04 CD will be just fine. Boot up with it, choose "try Ubuntu" to get to the live desktop, open a Nautilus file-browser and click on your Ubuntu root partition in the left pane. It will be mounted. Press ctrl-L and a text path will appear showing you the mountpoint for your Ubuntu partition. This will be either /media/<partition-label> if the partition has a label, or /media/<UUID> if not. (The UUID will be a very long alphanumeric string.) Now, in a terminal:

```
gksu gedit /media/mountpoint/etc/lightdm/unity-greeter.conf 
```

And edit the file back to how it should be. Obviously, change "mountpoint" to what you found in Nautilus.

---

### Post by Hulmemanitarian on 2011-10-31
Many thanks CoffeeCat! I've now been reunited with my favourite OS! Much appreciated!

---

