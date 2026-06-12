---
title: "Multiple Monitors"
date: 2010-01-25
forum: General Help
---

### Post by CrusaderAD on 2010-01-25
Can someone drop me some help on having multiple monitors in Kubuntu? I attached a screenshot. It recognizes both monitors, but it doesn't enable it, they're just mirrored. It works in Ubuntu... any ideas?

---

### Post by audiomick on 2010-01-25
Hi.
I don't use KDE, but: what do you get if you go down to the "multiple monitors" option that is visible in your screen shot?

---

### Post by SuperSonic4 on 2010-01-25
Also what video card/driver do you have? Multiple monitors is a doddle with nvidia

---

### Post by CrusaderAD on 2010-01-25
> **audiomick said:**
> Hi.
I don't use KDE, but: what do you get if you go down to the "multiple monitors" option that is visible in your screen shot?

Thanks for the replies. I did try this... it just says that it's not configured. No options. It's an ATI video card.

---

### Post by audiomick on 2010-01-25
Ok. I have nvidia, so I will run out of suggestions fairly quickly. First, obvious question: have you got the ATI driver installed?

---

### Post by CrusaderAD on 2010-01-26
> **audiomick said:**
> Ok. I have nvidia, so I will run out of suggestions fairly quickly. First, obvious question: have you got the ATI driver installed?

lol, no problem. I just have the default drivers installed. No proprietary drivers are in use, it doesn't detect anything. Dual monitors do work when I boot into Ubuntu, just not Kubuntu.

---

### Post by CrusaderAD on 2010-01-26
EDIT: it's only one ATI Radeon x1550 card. It has two ports for multiple monitors.

---

### Post by audiomick on 2010-01-26
> **raptormanad said:**
> One other thing, I completely forgot about this. I use two video cards. One on board (I think it's an intel) and one ATI X1550.

That makes it interesting...
Have you done
```
lspci
```
to make sure it the ATI card is being found. I daresay it is, as it works in Ubuntu, but have a look anyway.

---

### Post by CrusaderAD on 2010-01-26
Here's the output, looks like it does find it ok. Would the output be different in KDE?

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV505 [Radeon X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV505 [Radeon X1550 Series] (Secondary)
```

---

### Post by audiomick on 2010-01-26
> **raptormanad said:**
> Here's the output, looks like it does find it ok. Would the output be different in KDE?

Yes it is there. I can't imagine why it wouldn't show up in KDE. That is way below the GUI level, as far as I know.

---

### Post by CrusaderAD on 2010-01-26
It's weird. It shows both cards in the output, but in KDE it shows only one in the gui tool, even tho the monitors are connected to two completely different cards.

---

### Post by CrusaderAD on 2010-01-26
Update: I tried installing the AMD released drivers from their site. This is the result of their installer:

```
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-17-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.RYUbee

```

Also, when I launch the ATI control center I installed from the software center, it says No ati driver found.

---

### Post by CrusaderAD on 2010-01-27
Does anyone know what Kubuntu uses to configure the monitors? I don't see xorg anymore.

---

### Post by llawwehttam on 2010-01-27
did you try searching the forums?

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

Hope that helps.

---

### Post by CrusaderAD on 2010-01-27
Thanks for the reply. They keep referring to /etc/X11/xorg.conf... which doesn't exist on my system Kubuntu 9.10.

---

### Post by GameManK on 2010-01-27
On my system with the ATI card I installed the proprietary fglrx driver and the amd control center and used that.  That sets it up in Xorg.conf (which it creates, it's no longer used for a default setup).  Once that's done the KDE control module sees it too, but that's not terribly useful at that point.

If you just install fglrx via apt-get, and not the restricted drivers manager, you have to run something like ```
sudo aticonfig --initial
```to create xorg.conf and restart.

---

### Post by CrusaderAD on 2010-01-28
I installed the driver with the fglrx package and attempted to run ```
aticonfig --initial
```
This said no supported display adapters detected. Now Kwin crashes when I boot up! I did some looking around and it looks like ati drivers cause the kwin crash. I can't get into anything. Do I have to reinstall?

---

### Post by CrusaderAD on 2010-01-28
I got back to my original configuration. Whew. Still can't get dual monitors working.

---

### Post by CrusaderAD on 2010-01-28
Here's a screenshot of the settings in the Multiple Monitors tab. I'm using the ati x1550 radeon. I have this driver install by default for some reason:

xserver-xorg-video-intel

---

### Post by Untitled_No4 on 2010-01-30
There is nothing wrong with KDE in your screenshot, the feature you're looking for will be added in KDE 4.4 so there's nothing there in KDE 4.3.4 and before.

Fglrx doesn't work because your card is probably not supported by ATI anymore.

Basically what you need to do is:
1. Generate an xorg.conf file.
2. Edit it to match your system.
3. Tell X to use two screens.

It's not difficult but it's a lot of typing and since you last posted 2 days ago you might have found the solution yourself. If not, reply here and I'll tell you what you need to do.

---

### Post by CrusaderAD on 2010-01-30
Hey thanks for the input! Do you happen to have a sample xorg file I can use?

---

### Post by Untitled_No4 on 2010-01-30
Hey.

Better than a sample, make your own! Here's how:
- Logout from Kubuntu
- At the login screen, press alt + ctrl + F1 which will take you to a terminal.
- Login using your user/password and run the following commands:
```
sudo init 3
sudo X -configure
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf
sudo reboot
```

This will stop X and generate an xorg.conf file matching your hardware (and, obviously, copy it to the right location and then reboot).

If after reboot you have problems getting to the login screen of Kubuntu (you shouldn't have), you need to remove xorg.conf file.

Second step, you need to edit the file. When you're back into Kubuntu open a konsole and type the following:
```
xrandr
```

This will list your screens and their modes. Note the name of your two screens. This could be DVI-0 and DVI-1 or VGA-0 and DVI-0 or similar.

When you have that, to the fun part -- editing your xorg.conf file. Still in konsole
```
kdesudo kate /etc/X11/xorg.conf
```

This will be quite a long file, but the three sections that interest you are Device, Monitor and Screen (best delete the rest of the file). Here's my xorg.conf file as a reference:
```
Section "Device"
    Identifier  "ATI"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    Option      "Monitor-DVI-0" "Monitor 1"
    Option      "Monitor-DVI-1" "Monitor 2"
EndSection

Section "Monitor"
    Identifier  "Monitor 1"
EndSection

Section "Monitor"
    Identifier  "Monitor 2"
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Monitor     "Monitor 1"
    Device      "ATI"
    SubSection "Display"
      Depth           24
      # The size of the desktop in dual screens
      Virtual         2880 900
    EndSubSection
EndSection

```

What you need to edit is:
1. Put your screen names in the Option line of the Device section. My screens are called DVI-0 and DVI-1.
2. You should have two monitors sections, you can copy the above.
3. In the Screen section, change the device name to what you have under identifier in Device and change the value of virtual to the size of your desktop. I have two 1440 x 900 screens which are placed side by side, hence why my virtual screen is 2880 900.

When you've done that, save and restart X or reboot. At this point both screens might be working but in clone mode, although they might not. Open konsole and type again
```
xrandr
```

The screen which is set to virtual in xorg.conf should have a maximum size as you put in xorg.conf. Here's mine:
```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 2880 x 900
DVI-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 410mm x 257mm
.
.

```

If that's not the case you have to figure out why (e.g. have you really restarted X?). If all is well, you can move on, still in Konsole, type:
```
xrandr --output DVI-0 --auto --left-of DVI-1
```
Change DVI-0 and DVI-1 to the names of your screens.

And this should be it. Your next question is going to be how to make the change permanent. Well, open konsole and type
```
kdesudo kate /etc/X11/Xsession.d/45custom_xrandr-settings
```

type your xrandr into the file, save, and it will run every time you boot computer.

Good luck!

** Just to be on the safe side. If ever during that process you run into display problems you need to remove or rename xorg.conf and see what you've done wrong. The commands are:
```
sudo rm /etc/X11/xorg.conf
``` to delete the file or ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bad
``` to rename it.

---

### Post by Untitled_No4 on 2010-01-30
Oh, and just for your knowledge, in Lucid none of this will be necessary (or rather, shouldn't be). The screens' settings are automatically detected, so no need for xorg.conf, and KDE 4.4's system setting allows you to set the relative location of the screens from the display entry (what you couldn't find now).

---

### Post by CrusaderAD on 2010-01-30
Awesome! Thanks for the super detailed post! I'll give this a try and post my results here afterwards. Hopefully Lucid comes through later on.

---

### Post by Untitled_No4 on 2010-01-30
Let me know how you get along. Lucid will be here eventually, at the moment it's still hazy.

---

### Post by CrusaderAD on 2010-02-01
When I get to:

```
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf
```

It says no file or directory.

---

### Post by Untitled_No4 on 2010-02-01
When you run sudo X -configure, if it completes successfully it should say that an xorg.conf.new file was created (and the location of it). If it can't generate one, then it should give you an error.

Let's try and skip that step though. Please post the output of ```
xrandr -q
```
And I'll try get modify my xorg.conf for your machine.

---

### Post by CrusaderAD on 2010-02-01
Thanks! Here's the output...

```
DVI-1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0     59.9*
   1280x1024      75.0     60.0
   1152x864       75.0
   1024x768       75.0     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     59.9
   720x400        70.1
DVI-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9 +   75.0     59.9*
   1280x1024      75.0     60.0
   1152x864       75.0
   1024x768       75.0     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     59.9
   720x400        70.1

```

I appreciate the help!

---

### Post by CrusaderAD on 2010-02-01
This was the output for sudo X -configure:

```
Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.

 ddxSigGiveUp: Closing log

```

---

### Post by Untitled_No4 on 2010-02-01
The error means that ```
sudo init 3
``` didn't close X properly, we can probably overcome that.

Try saving the following to as /etc/X11/xorg.conf:
```

Section "Device"
	Identifier  "ATI"
	Option 	    "Monitor-DVI-0" "Monitor0"
	Option      "Monitor-DVI-1" "Monitor1"
EndSection

Section "Monitor"
	Identifier  "Monitor0"
EndSection

Section "Monitor"
	Identifier  "Monitor1 "
EndSection

Section "Screen"
	Identifier "Screen0"
	Monitor    "Monitor0"
	Device     "ATI"
	SubSection "Display"
		Depth     24
		Virtual	  2880 900
	EndSubSection
EndSection
EndSection

```

and then restart x.

If the screens don't work just delete /etc/X11/xorg.conf and restart x. 
If they (or one) work run xrandr -q again. The first line should show something like that:
```

Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 2880 x 900

```

Maximum is the thing to look for here. If it's says 2880 x 900 (or larger) xorg.conf is configured properly, if it's below that something is not configured right.

Hope it works!

---

### Post by CrusaderAD on 2010-02-01
Hm, this didn't work. It took me to the "Ubuntu is running in low graphics mode" screen. Bummmer. Maybe xorg needs to be generated like you suggested?

---

### Post by Untitled_No4 on 2010-02-01
Before you do that, try to delete the last line in my suggested xorg.conf file (EndSection) since it shouldn't be there. 

Hopefully that will be it... If not, you can either generate an xorg.conf file -- you just have to make sure Xserver isn't running (sudo init 3 should take care of that if you're on Karmic or earlier), but you could also just try and figure out what's wrong by elimination -- i.e. commenting everything in that xorg.file besides the Device section and seeing if you still log into low graphics mode.

---

### Post by CrusaderAD on 2010-02-01
It came back up with no problems using the new xorg file, but the monitors are still mirrored. Here's what xrandr -q had to say:

```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 2880 x 900

DVI-1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0     59.9*
   1152x864       75.0
   1024x768       75.0     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     59.9
   720x400        70.1
DVI-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9 +   75.0     59.9*
   1152x864       75.0
   1024x768       75.0     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     59.9
   720x400        70.1

```

---

### Post by Untitled_No4 on 2010-02-01
That's good.

Now try:
```

xrandr --output DVI-0 --auto --right-of DVI-1

```

This assumes that DVI-0 is left of DVI-1. If that's not the case (you might need to run it first to be know) just change --right-of to --left-of.

---

### Post by CrusaderAD on 2010-02-01
Bingo! Thank you! Thank you! Thank you!

---

### Post by Untitled_No4 on 2010-02-01
Glad it worked.

That last xrandr command, you will have to run it every time you restart x, or you can save it to /etc/X11/Xsession.d/45custom_xrandr-settings and it will run automatically every time you log in.

---

### Post by duh FooL on 2010-02-25
I stumbled on this thread and it helped solved my issues.
I did notice that if I go to System Settings -> Display, it negated the xrandr command and reverted back to mirroring display 0 on both monitors.

Is there a way to avoid that or is the Display control panel not that smart?
I am using the KDE desktop on Karmic.

---

### Post by Untitled_No4 on 2010-02-25
Not that I know of, sorry. I just avoided going into that module since it was not that useful in KDE < 4.4.

---

