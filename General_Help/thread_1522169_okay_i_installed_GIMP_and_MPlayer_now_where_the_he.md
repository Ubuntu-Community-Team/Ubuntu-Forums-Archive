---
title: "okay i installed GIMP and MPlayer now where the hell is my icon?"
date: 2010-07-01
forum: General Help
---

### Post by ThirdEye4103 on 2010-07-01
title says it all ^^^^^^         what the hell?

---

### Post by drs305 on 2010-07-01
It doesn't quite tell us all. Are you trying to find how to start GIMP, or do you want to know where the icon file is?

To start GIMP: Main Menu or Applications, Graphics, GIMP.
From there, you can also right click on the GIMP icon to get an option to put it on your Desktop or panel.

The icon itself (at least one of them) is located at */usr/share/icons/hicolor/48x48/apps/gimp.png*

I don't use MPlayer but assume it would be Main Menu or Applications, Sounds.

---

### Post by WorMzy on 2010-07-01
GIMP: [Applications -> Graphics -> GIMP Image Editor]("http://www.ubuntu-pics.de/bild/94713/screenshot_086_EklQns.png")
MPlayer: [Applications -> Sound & Video -> MPlayer Media Player]("http://www.ubuntu-pics.de/bild/94716/screenshot_087_bj9T1F.png")

---

### Post by ThirdEye4103 on 2010-07-01
yeah sorry for not being as specific, but yeah i figured it would be exactly there, and neither of them are located in those sections. so i have no way to launch either program.

---

### Post by J V on 2010-07-01
Rightclick the menu and hit edit: Check if they're there (If they are, check them so they will be visible)

---

### Post by drs305 on 2010-07-01
> **ThirdEye4103 said:**
> yeah sorry for not being as specific, but yeah i figured it would be exactly there, and neither of them are located in those sections. so i have no way to launch either program.

That's what we assumed you meant, but sometimes users want other things.

First, right click on the menu, Edit Menu, and see if they are there and enabled for viewing.

If not, have you checked to see if they are really installed via Synaptic?

You can also open a terminal (Applications, Accessories, Terminal) and run these commands to see if the executables are installed:

```
which gimp
*should return:  /usr/bin/gimp*
which mplayer
*should return:  /usr/bin/mplayer*
```

If those values are returned, your next step may be to just type in the command (e.g. /usr/bin/gimp, although "gimp" should also work) in a terminal, press ENTER, and see if it runs.

If you get those returns, you can always try to make a shortcut manually. Right click on the upper panel, "Add to Panel". First see if they are listed by clicking "Application Launcher" and look under "Graphics" (gimp) and "Sound & Video" (mplayer).

If they aren't there but the commands above returned the proper value, you can click on the "Custom Application Launcher". The command line would be "/usr/bin/gimp" and "/usr/bin/mplayer".

---

### Post by ThirdEye4103 on 2010-07-01
neither are there either.

---

### Post by drs305 on 2010-07-01
> **ThirdEye4103 said:**
> neither are there either.

Try installing them from the command line:
```
sudo apt-get install gimp mplayer
```

If you get an error, first check your repositories by opening Synaptic or Software Sources (System, Administration, ...), Settings, Repositories and ensure the universe and multiverse repositories are enabled. Hit "Reload" from the app's main menu. If you are in Synaptic, you might as well try to install them from there instead of returning to the command line.

---

### Post by ThirdEye4103 on 2010-07-01
okay i thought i found the problem, i added the packages in synaptic from a flash drive, and installed directly from the flash drive and when i unplugged it, they were not  listed as installed in synaptic, so i did it again but i moved the folder to my computer. it says there installed, but when i enter that in terminal i dont get anything back besides the folder for mplayer. and they are still not in the edit menu.

---

### Post by drs305 on 2010-07-01
> **ThirdEye4103 said:**
> okay i thought i found the problem, i added the packages in synaptic from a flash drive, and installed directly from the flash drive and when i unplugged it, they were not  listed as installed in synaptic, so i did it again but i moved the folder to my computer. it says there installed, but when i enter that in terminal i dont get anything back besides the folder for mplayer. and they are still not in the edit menu.

Assuming you have an internet connection, remove the flash drive and reinstall them from Synaptic or the command line. Just moving the folder to your main drive won't register the applications with the package manager. Reinstalling them (or actually installing them on the main drive for the first time) will allow the system to know exactly where the files now reside. 

If you don't have an internet connection but do have the packages *.deb* file, move it to your Desktop and double click it to install.

---

### Post by ThirdEye4103 on 2010-07-01
okay i got GIMP working and showing up by doing that, thanks alot buddy.

---

### Post by mc4man on 2010-07-01
The mplayer package  in lucid is cli and no longer contains a gui so there won't be a menu item 

If you wish a gui then install gnome-mplayer (simple), or smplayer (more full featured.
(or try both and see

Edit : and both are highly superior to the old gui gmplayer - if for some reason you have/get

---

### Post by ThirdEye4103 on 2010-07-01
okay cool, thanks guys. you guys rock. i greatly appreciate you handling my n00b bitching.

---

