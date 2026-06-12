---
title: "Screen resolution problem"
date: 2012-03-08
forum: General Help
---

### Post by kimikelku on 2012-03-08
Hello everyone.
I have a core quad 6600 with a nvidia 8600gt and a screen with 1280x1024 res.
I have installed Windows 7, and i installed ubuntu from the cd to dual boot the 2 OS.
The problem is my resolution is stuck at 1280x768 and i cant make it to 1280x1024.
I have been searching for a solution but non have worked so far.
So if anyone can help me, thx in advance.

---

### Post by kimikelku on 2012-03-08
Anyone can help me?
Bump!

---

### Post by gordintoronto on 2012-03-08
What version of Ubuntu? Did you install any "Additional Drivers"? What brand and model of monitor? Is it connected by a VGA cable?

---

### Post by papibe on 2012-03-08
Do you get the correct resolution on Windows?

It may be possible to get the monitor info from there and 'import it' (sort of speak) to Ubuntu.

Regards.

---

### Post by pqwoerituytrueiwoq on 2012-03-08
assuming you can't set the right resolution in nvidia-settings
post output of
[FONT=Courier New]sudo Xorg -configure;cat ./xorg.conf[/FONT]
we should be able to manually force the resolution

---

### Post by kimikelku on 2012-03-09
Thx all for yout time,
Now by question:
Ubuntu 11.10, still didnt install anything just the OS itself, its a LG L1715S connect by vga.
In windows i get the correct resolution.
And the output of that command:

```
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```

---

### Post by kimikelku on 2012-03-09
Quick update, in the nvidia configuration i manually set the resolution to 1280x1024 and it saved to the xorg.conf file.
I hit aplly and the screen blinks for a second, then i went to the monitor settings and i see the option 1280x1024 5:4, i choose it and i hit aplly, and i get an error saying that it cant aplly, minimum 320, 240  maximum  1024, 768.

---

### Post by sudodus on 2012-03-09
Please post the output of the command
```
xrandr
```
It should show available screen resolutions. You can read about that command in ```
man xrandr
```

---

### Post by Grenage on 2012-03-09
Hi, kimikelku; give this a whirl.

First make sure that you have either a Linux livecd/Ubuntu CD, or are comfortable logging into a terminal - just in case something goes wrong and you can't get a GUI.

1) Move your old xorg.conf:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup
```

Now open a new one (we'll use gedit):

```
gksu gedit /etc/X11/xorg.conf
```

Paste in the following config, and save it.  I have assumed that you are using the open 'nouveau' driver; if you're using the proprietary driver (enabled under 'additional drivers'), then replace 'nouveau' with 'nvidia'.

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "LG"
	ModelName "L1715S"
	HorizSync 30 - 83
	VertRefresh 56 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nouveau"
	VendorName "nvidia 8600gt"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

Reboot your PC; if something goes wrong, you can delete the new config file and rename the old one.  Let us know if that works, or not.

---

### Post by kimikelku on 2012-03-09
> **Grenage said:**
> Hi, kimikelku; give this a whirl.

First make sure that you have either a Linux livecd/Ubuntu CD, or are comfortable logging into a terminal - just in case something goes wrong and you can't get a GUI.

1) Move your old xorg.conf:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup
```Now open a new one (we'll use gedit):

```
gksu gedit /etc/X11/xorg.conf
```Paste in the following config, and save it.  I have assumed that you are using the open 'nouveau' driver; if you're using the proprietary driver (enabled under 'additional drivers'), then replace 'nouveau' with 'nvidia'.

```
Section "Monitor"
    Identifier "Monitor0"
    VendorName "LG"
    ModelName "L1715S"
    HorizSync 30 - 83
    VertRefresh 56 - 75
EndSection

Section "Device"
    Identifier "Device0"
    Driver "nouveau"
    VendorName "nvidia 8600gt"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1280x1024"
    EndSubSection
EndSection
```Reboot your PC; if something goes wrong, you can delete the new config file and rename the old one.  Let us know if that works, or not.

After doing that and reboot when it shows the boot screen it goes black and it shows some processes starting but it doesnt boot, i can only restart it.

---

### Post by Grenage on 2012-03-09
Greetings,

Are you using the proprietary driver (additional drivers)?  If so can you change the driver referenced in the config file to "nvidia", rather than "nouveau" and try again?

You can edit the file either though a terminal (ctrl-alt-F1) or using a livecd.

---

### Post by kimikelku on 2012-03-11
Did that, but now i cant even get to the password screen it just shows some info about some processes starting and i cant get it on.

---

### Post by kimikelku on 2012-03-12
This is what i get after the boot animation, cant go futher then this screen:

[IMG]http://i.imgur.com/m5JlZl.jpg[/IMG]

---

### Post by sudodus on 2012-03-12
I don't know how to repair your system now, I think other people know better how to do that.

In the meantime, I suggest that you boot a live session from your Ubuntu install CD or USB drive. Do not install anything to your HDD, only run in that live session ***xrandr*** and post the result in a reply!

> **sudodus said:**
> Please post the output of the command
```
xrandr
```It should show available screen resolutions. You can read about that command in ```
man xrandr
``` This would give us some information making it easier to help.

---

### Post by Grenage on 2012-03-12
If you're using the proprietary driver (additional drivers section), and the xorg.conf with the "nvidia" driver is causing tho above, delete the config file and reboot.

You can either try the xrandr angle, as per sudodus' post, or you can try one of the alternative drivers listed in 'additional drivers'.

---

### Post by kimikelku on 2012-03-12
Again thx for your time.
Ok, before i posted here i tryed every option in the "additional drivers" non worked. I tryed to install manually the nvidia drives from the site, but i got a mensage saying that i needed to install it has sudo, im pretty new to linux so i dont know the commands to do it.
About the boot problem, i know its because of that new xorg.conf i created but like i said im new so i dont know the commands to delete this xorg.conf and restore the xorg.backup, so if you can guide me, i appreciate.

---

### Post by Grenage on 2012-03-12
No problem at all; you have two ways to go about this, you can either boot the Ubuntu CD and delete the file via the GUI, or you can do it via a local terminal.

To delete the file via the CD GUI, you simply boot from it, then go to your home folder/file browser, and click on the icon for your local drive (top left, under devices).  Browse to the etc/X11 directory on the drive, and delete xorg.conf.

To delete via the terminal, when the boot fails, try pressing Ctrl-Alt-F1.  That should give you a login prompt, which you can then use to delete the file:

```
sudo rm /etc/X11/xorg.conf
```

---

### Post by kimikelku on 2012-03-13
Ok run into another problem, in the terminal when i try that command its says that the file is read only.
With the live cd i cant edit or delete the file.

---

### Post by Grenage on 2012-03-13
Hi again,

You are prefixing the *rm* command with *sudo*, I assume?  When using the CD GUI, make sure you're accessing /etc/X11/xorg.conf on your local hard drive - click on the drive icon in the top seft of the file browser.  The 'virtual' CD install will probably have its own /etc/X11/xorg.conf, and I doubt it will let you delete that.

---

### Post by kimikelku on 2012-03-13
Its not in English but you can see that i cant rename or delete it with the live cd

[IMG]http://i.imgur.com/JTOyx.png[/IMG]


if i try to access it from the terminal. it says that the file doesnt exist, so i cant change its permissions.
This is in the live cd,

[IMG]http://i.imgur.com/ZxSG5.png[/IMG]

 But in the image above this one, it shows that the file is there but i cant see it in the terminal.
I dont know if i do this commands if it apllys in the files from the cd or from the hard drive it self, but  even from the terminal when i press ctrl alt F1  in the boot screen it says the same, cant find file or directory.

---

### Post by Grenage on 2012-03-13
I have no idea why xorg.conf wouldn't be present when logging in via the terminal.

The terminal when you've booted from the CD will not show an xorg.conf, as it's looking at the virtual install.  Try running the file manager with sudo, and see if you can delete it:

```
gksu nautilus /etc/X11
```

---

### Post by sudodus on 2012-03-13
> **Grenage said:**
> I have no idea why xorg.conf wouldn't be present when logging in via the terminal.

The terminal when you've booted from the CD will not show an xorg.conf, as it's looking at the virtual install.  Try running the file manager with sudo, and see if you can delete it:

```
gksu nautilus /etc/X11
```

(and may I fill in) ...and remember to move to the 'Sistema de arquivos de 19 GB' partition and remove the file or directory in

```
/media/.../etc/X11
```

---

### Post by Grenage on 2012-03-13
Ah, thank you for picking up on that oversight!

---

### Post by kimikelku on 2012-03-13
Im a little lost now, if i do what Grenade said, it shows the files from the live cd, how do i access the partition were ubuntu is installed with that command?
I know that sudodus is talking about that but i dont know how to do it, sry, im pretty nab about this.

---

### Post by Grenage on 2012-03-14
I typo'd and sudodus picked up on it, sorry about that.  To start with, just run nautilus as with sudo:

```
gksu nautilus
```

Then browse to your /media directory, and there should be a directory for each partition on the computer.  Enter the partition with your Ubuntu install, and then go into the etc/X11 directories there.

Does that make more sense?

---

### Post by kimikelku on 2012-03-14
Ah ok i tough i didnt understand that part from sudodus, but it looks like i did, but i only saw the cdrom drive in it, no partitions, another problem :/
Its giving alot of trouble, so ill format my pc and do another fresh install, so i can get back to the main problem from this topic.
Again thx for your help.

---

### Post by sudodus on 2012-03-14
Please make it easier for you by testing some versions and flavours of Ubuntu ***live*** booted from a CD or USB drive before deciding what to install! You can also 'install' the built-in proprietary graphics drivers to the live session and find out if they work.

---

### Post by Fond on 2012-04-10
This is what I did
1. enter command in terminal                      cvt 1280 1024
   you get something similar to this 
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline [COLOR=Red]"1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync[/COLOR]
2. enter command in terminal                      xrandr
   you get something similar to this 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 disconnected (normal left inverted right x axis y axis)
[COLOR=Blue]DVI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm[/COLOR]
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
S-video disconnected (normal left inverted right x axis y axis)
3. enter command in terminal     gksudo gedit /etc/gdm/Init/Default
editor will popup
and just under line 

PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

_enter this 3 line_

xrandr --newmode[COLOR=Red] "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync[/COLOR]

[COLOR=Blue]xrandr --addmode DVI-0 1280x1024_60.00

xrandr --output DVI-0 --mode 1280x1024_60.00[/COLOR]

save exit restart

red line copy from output of your first command just behind _Modeline_
second command define which output you using  (2 monitor, s video, vga etc...)

THIS OUTPUT AR FOR MY PC SO WATCH FOR YOUR OUTPUT. 

hope will help

---

