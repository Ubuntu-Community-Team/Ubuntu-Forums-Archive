---
title: "Karmic desktop size problem"
date: 2009-11-01
forum: General Help
---

### Post by Cirbre on 2009-11-01
Using ATI restricted drivers (newest 9-10 from ATI's website), installed Karmic yesterday. One 22" Samsung monitor. Compiz effects (including Cube) enabled.

Problem: the system seems to translate desktop size wrong.

Starts already in GDM, login screen displayed, but on it's "right side" is a completely blank screen. Can move there by moving mouse cursor.

When Gnome loaded, at first behaves similarly, ie. on the right side of the screen can move to an empty screen (has the background, though). At some point (after starting an application?) this "second desktop" is disabled, ie. can no longer move there with a mouse.  

The wallpaper is always displayed as being stretched over this "double desktop". Using the scaled option it only displays half of it's size in the right half of the screen.

In the workspace changer the size of one desktop is presented as having double width. Cannot change to the "other half" from workspace changer, or with mouse wheel from the desktop. Interestingly, otherwise can navigate to the second desktop utilizing cube movements. In workspace changer the "active" desktop remains the same.

Anybody else had the same problem? Any solutions?

---

### Post by DeMus on 2009-11-01
> **Cirbre said:**
> Using ATI restricted drivers (newest 9-10 from ATI's website), installed Karmic yesterday. One 22" Samsung monitor. Compiz effects (including Cube) enabled.

Problem: the system seems to translate desktop size wrong.

Starts already in GDM, login screen displayed, but on it's "right side" is a completely blank screen. Can move there by moving mouse cursor.

When Gnome loaded, at first behaves similarly, ie. on the right side of the screen can move to an empty screen (has the background, though). At some point (after starting an application?) this "second desktop" is disabled, ie. can no longer move there with a mouse.  

The wallpaper is always displayed as being stretched over this "double desktop". Using the scaled option it only displays half of it's size in the right half of the screen.

In the workspace changer the size of one desktop is presented as having double width. Cannot change to the "other half" from workspace changer, or with mouse wheel from the desktop. Interestingly, otherwise can navigate to the second desktop utilizing cube movements. In workspace changer the "active" desktop remains the same.

Anybody else had the same problem? Any solutions?

Disable Compiz and effects and try again. Compiz is known to play tricks with graphics, tricks you don't want.

---

### Post by Cirbre on 2009-11-01
> **DeMus said:**
> Disable Compiz and effects and try again. Compiz is known to play tricks with graphics, tricks you don't want.

Didn't help. A correction on the original report though: in Gnome the "right part desktop" _doesn't_ have background. Also, it is indeed blocked out when I open a window/application. After that I cannot move the cursor back there, although it stays in view until I completely scroll to the "correct" desktop. After that I can no longer move there, although it does seem to still "exist".

It's almost if there was some ghost monitor connected, ie. screen size set to a double, but desktop width only to single or some other combination like that.

---

### Post by DeMus on 2009-11-01
Can you send us a screenshot? Maybe that makes things clearer.

---

### Post by P4man on 2009-11-01
Despite your heroic efforts Im having a hard time picturing whats going on. Does a screenshot explain it? Or perhaps a camera picture of your monitor>

---

### Post by Cirbre on 2009-11-01
> **DeMus said:**
> Can you send us a screenshot? Maybe that makes things clearer.

Woah... Now that was interesting... Doesn't really give me any additional idea what's wrong though, but it does verify the "other desktop's" existence.

---

### Post by Cirbre on 2009-11-01
Sorry, I really didn't realize it'd show on a screengrab before I tried it out. I thought it would only show when playing with a mouse at the start, and then only in the workspace changer or something. 

By the way, the problem starts already in the GDM (login screen), so I don't think it's related to Compiz (Compiz is started only after loading the main Gnome desktop, right?).

---

### Post by P4man on 2009-11-01
In the catalyst control center does it show 2 monitors? What desktop size does it show?

---

### Post by Cirbre on 2009-11-01
One monitor only, Multi-display set to Single. Desktop area "Preferred". Returns always to this even if I set it to the monitor's max (preferred) size.

---

### Post by DeMus on 2009-11-01
> **P4man said:**
> In the catalyst control center does it show 2 monitors? What desktop size does it show?

When I saw that picture that was my first idea as well. But the OP says it is set to one monitor only.
What else can it be? Can it be the 16:9 and 4:3 formats being wrong somewhere? Maybe mixing up both of them.
Can you open a graphical program and draw a circle there. Is it a circle or more like an eclipse?

---

### Post by simpleeddie on 2009-11-01
can you post the contents of you /etc/X11/xorg.conf file please?

---

### Post by Cirbre on 2009-11-01
A drawn circle does indeed look like a circle. Also, I don't think it's a 4:3 / 16:9 -format problem, since the difference seems to be entirely horizontal. 

```


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
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

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	Monitor    "amdcccle-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```


Do I read that right, does it say I have two monitors?

---

### Post by JBAlaska on 2009-11-01
On the lower right side of your visible screen...see the 2 desktops? right click on them and choose 1..I believe that starting with Karmic that compiz starts before the login screen..I think desktop wall is enabled and your virtual desktops are set to 2.

Doing what I suggested should prove or disprove this..then we can easily fix it..

Edit ..Now that I look at your xorg.conf. I think I was wrong..

Two choices at this point imo..
1- Run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And give it another chance to detect your single monitor correctly or..
2- Backup than edit xorg.conf and remove the entries relating to monitor and device 1

Then restart x

---

### Post by simpleeddie on 2009-11-01
sudo dpkg-reconfigure -phigh xserver-xorg

try this code first, I know it is a futile attempt to fix your problem but it is worth a try.

Personally I have a NVida card, and know the NVida way of doing things best. First up, I would recommend you try and remove your current ATI drivers and reinstall them using EnvyNG (unless you did this originally). I'm not sure about ATI, but I have heard some terrible things about installing the nvidia drivers from the website, by hand.

Next, copy your xorg.conf and rename that copy xorg.conf.backup

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup  should do the trick.

then go into your ATI editor and try setting your settings again, and save as usual. 

***Important - Before you log off, or restart X, or do anything, ensure that the ATI Control Center has rewritten a new xorg.conf file, and has filled out the required information (read 'anything')

After you are sure that you have an xorg.conf file and a xorg.conf.backup file, reboot X server

 sudo /etc/init.d/gdm restart

let me know how this goes

---

### Post by Cirbre on 2009-11-01
JBAlaska: Tried out the option 1, and it didn't seem to do anything. Rebooted the machine too, and no change in desktop. Xorg.conf also seems to be the same.

---

### Post by simpleeddie on 2009-11-01
best bet is to try the second option. I know that is is a little harder but this is the same solution to my problem today, so I am sure it will work for you.

---

### Post by P4man on 2009-11-01
You have a virtual desktop that is way bigger than your actual. Surprisingly tho it doesnt show in xorg.conf. Look long and hard at your setting in the catalyst control center.

---

### Post by Cirbre on 2009-11-01
> **simpleeddie said:**
> sudo dpkg-reconfigure -phigh xserver-xorg

try this code first, I know it is a futile attempt to fix your problem but it is worth a try.

Personally I have a NVida card, and know the NVida way of doing things best. First up, I would recommend you try and remove your current ATI drivers and reinstall them using EnvyNG (unless you did this originally). I'm not sure about ATI, but I have heard some terrible things about installing the nvidia drivers from the website, by hand.

Next, copy your xorg.conf and rename that copy xorg.conf.backup

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup  should do the trick.

then go into your ATI editor and try setting your settings again, and save as usual. 

***Important - Before you log off, or restart X, or do anything, ensure that the ATI Control Center has rewritten a new xorg.conf file, and has filled out the required information (read 'anything')

After you are sure that you have an xorg.conf file and a xorg.conf.backup file, reboot X server

 sudo /etc/init.d/gdm restart

let me know how this goes

Did this, and the xorg.conf file looks now better, but still didn't fix the desktop size problem :(

New xorg.conf:
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by JBAlaska on 2009-11-01
[COLOR="Blue"]Edit: you were faster than I was..[/COLOR]

Try to  rename xorg.conf to xorg.conf.bak and restart x.

If that does not work..you may have to resort to reinstalling your ati drivers.

You don't by any chance have a duel GPU card or a crossfire setup do you?

Since I gave up on Ati cards in Linux after my 9800 XT, I'm sorry I can't be of more help.

---

### Post by Cirbre on 2009-11-01
> **P4man said:**
> You have a virtual desktop that is way bigger than your actual. Surprisingly tho it doesnt show in xorg.conf. Look long and hard at your setting in the catalyst control center.

Virtual desktop might indeed be the case, but couldn't find any specific setting for it in the Catalyst.

But, did discover something strange: 

Changed the desktop resolution in Catalyst to a value _smaller_ than the preferred/maximum resolution, and that appears to have corrected the problem (screengrab normal, workspace picker works, wallpaper scales correctly). Returned the resolution back to maximum, and everything still okay! 

But alas, after a restart, the problem is back. And the "fix" is a bit of a clunker if it doesn't stick :(

---

### Post by P4man on 2009-11-01
Try adding this red line.
Change the 1280 1024 to whatever your resolution is
```
 <snip>
Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24

	SubSection "Display"
		Viewport   0 0
		Depth     24
[COLOR="DarkRed"]               **Virtual 1280 1024**[/COLOR]
	EndSubSection
EndSection

```

---

### Post by JBAlaska on 2009-11-01
It's got to be related to the Xinerama option even though it's set to off...I still think Karmic should boot the gui without a xorg.conf...

---

### Post by Cirbre on 2009-11-01
> **P4man said:**
> Try adding this red line.
Change the 1280 1024 to whatever your resolution is


No change :(

---

### Post by JBAlaska on 2009-11-01
If you don't want to try booting without a xorg.conf...just comment out the Xinerama option line and save.

Restart x and try that..

Although I think "Viewport   0 0"  Looks fishy also

---

### Post by simpleeddie on 2009-11-01
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "0"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
        VendorName   "ATI Proprietary Driver"
	ModelName    "Generic Autodetecting Monitor"
	Option	     "DPMS" "true"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection
```

Note some of the edits I have made in this file. Repeat backup procedure, then ```
sudo gedit /etc/X11/xorg.conf
```

replace current selection with my edit above. restart x as usual. 

***BTW: if you get stuck, and X won't start, press alt-f6, login, type sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf and press alt-f7, or reboot. this will reset your current (apparently broken) file to the backup and restore your use of X.***

my changes are minor, and if they do not have any impact, then the problem will lie in the driver, and you will need to reinstall a different version, or reinstall the current one.

**just a side note, if you go to system>preferences>display does it let you make changes? or does it say something about a propriety driver and not let you really do anything. if the first option is the case, that may also be contributing to our problem.

---

### Post by JBAlaska on 2009-11-01
Looks good eddie..no "Viewport   0 0" and Option "Xinerama" "0" , But I think commenting out Xinerama will work also.

[COLOR="Red"]Edit: reading wildly on google and Option "Xinerama" "false" is the proper syntax[/COLOR]

---

### Post by Cirbre on 2009-11-01
Been playing around with the system, and a few things I've noticed:

1) the free "ati" driver works correctly
2) trying to install ATI restricted drivers via EnvyNG borks up the system. Only the drivers fetched from ATI site seem to work (haven't tried out the Ubuntu recommended drivers though)
3) it seems that xorg.conf is read when GDM (login screen) starts

It really seems like the ATI restricted drivers are the culprit. Still no clear reason as to why this happens, but from the earlier steps taken it seems to be related to desktop size / virtual desktop. Will need to do some more tests..

---

### Post by P4man on 2009-11-01
> **Cirbre said:**
> 
2) trying to install ATI restricted drivers via EnvyNG borks up the system. Only the drivers fetched from ATI site seem to work (**haven't tried out the Ubuntu recommended drivers though**)

why oh why?

---

### Post by JBAlaska on 2009-11-01
Really, try the Ubuntu recommended drivers, and I think simpleeddie's modded xorg.conf is gonna work with the addition of Option "Xinerama" "false"...


Gotta be bloody "Xinerama"

---

### Post by Cirbre on 2009-11-01
> **simpleeddie said:**
> 

replace current selection with my edit above. restart x as usual. 

my changes are minor, and if they do not have any impact, then the problem will lie in the driver, and you will need to reinstall a different version, or reinstall the current one.

**just a side note, if you go to system>preferences>display does it let you make changes? or does it say something about a propriety driver and not let you really do anything. if the first option is the case, that may also be contributing to our problem.

Tried this xorg.conf out, and the problem still persists. system>preferences>display complains about hardware producer's drivers, but lets open the setting window. An interesting point: this lists the resolution 3360X1050. Choosing it doesn't seem to help in this problem, but it's interesting to notice that something like this exists here (Catalyst doesn't offer this resolution).

It really seems that the ATI restricted drivers are the problem. I'll continue using this version for now and just change resolutions/desktop size manually when I turn the computer on. Hopefully there will be a solution or a fixed driver soon...

Thank you to everyone for helping me here! Solutions and suggestions are still welcome!

---

### Post by Cirbre on 2009-11-01
> **P4man said:**
> why oh why?

Because the version offered was an older version than the one I've been using on Jaunty this Autumn, since the older versions caused me problems that were only fixed in the newer drivers.. Might try it out though, but gotta postpone that until evening..

UPDATE!

Yeah, tried out installing the ATI restricted drivers recommended by Karmic's own restricted drivers manager, and the whole xserver pretty much melted (couldn't get it working again, just don't have enough skills to do that from command line). So I ended up completely re-installing Karmic from an installation CD and then installing the version of fglrx Karmic recommends. And at least for now all seems to be working. As an interesting aside: Catalyst won't start, but crashes. On the other hand, the System->Preferences->Display -window works..

Oh well, my problem may well have been either a fluke, or a bug in the newest Catalyst drivers. In either case, there probably isn't much that can be made right now, so I'm dropping this (for now).

A big, heartful thanks to everyone trying to solve this one with me! Your help is greatly appreciated!

---

### Post by psm22 on 2009-11-03
I have the same issue here. First of all, my default display manager changed to xubuntu. I've changed back to gnome, but my desktop still seems to be larger than my screen. It's really annoying because every time my mouse hits a toolbar, the whole desktop shifts. 

My recommended nvidia driver is enabled. I've tried changing it with envyng but no go.

My nvidia xserver settings say the display is 1280 x 1024 as it should be.

---

### Post by crudh on 2009-11-06
I have the same problem with the ATI Catalyst drivers and have found no solution. Every time i log in I have to run "xrandr -s 1680x1050" to get the correct desktop size.

---

