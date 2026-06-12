---
title: "Only able to boot  graphic failsafe mode after making changes"
date: 2011-08-05
forum: General Help
---

### Post by higashi on 2011-08-05
In an attempt to get pressure sensitivity to work on my Wacom tablet, I followed [this guide]("http://ubuntuforums.org/showthread.php?t=765915"). Shortly after completing it, I realised that the guide was outdated.
Now, every time I try to boot Ubuntu 11.04 (with Gnome3 desktop), all I get is a blank screen. (the back light is still working though)

The only way I'm able to boot into ubuntu at all now is if I select recovery mode from the boot menu and then select graphic failsafe mode.

---

### Post by Favux on 2011-08-05
Did you edit the xorg.conf as the guide shows?  Was there an xorg.conf already there or did you create one?

---

### Post by higashi on 2011-08-06
I created one, and just entered what was in the guide

---

### Post by Favux on 2011-08-06
Good, that should be easy to fix.  Boot up in Recovery Mode and get to a command line.  Then enter:
```
sudo nano /etc/xorg.conf
```
While in the nano editor comment out every line you put in the xorg.conf.  In other words place a # in front of each line.  I'd rather do that than remove the xorg.conf because I'd like to see it and verify there isn't anything you need in it.  Then save it and reboot.

---

### Post by higashi on 2011-08-06
I entered the command and there was nothing to comment out (it was just blank). I then checked in /etc/ for the xorg file and it wasn't there.

If I search "xorg.conf" in my file search, It gives me the following results:
Name..............................Folder
xorg.conf ......................  /etc/X11
xorg.conf.failsafe ............... /etc/X11
xorg.conf ......................../home/me
xorg.conf.d ....................../usr/share/X11
xorg.conf ......................../usr/share/doc/xserver-xorg-video-nouveau/examples
xorg.conf.5.gz ..................../usr/share/man/man5

---

### Post by Favux on 2011-08-06
Sorry, my goof, I left out X11:
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by higashi on 2011-08-06
I followed your instructions and it still won't work.
Also now my track pad seems to have stopped working :\

---

### Post by Favux on 2011-08-06
The touchpad should be configured in xorg.conf.d.  You don't need a synaptics entry in xorg.conf to get it to work.  So are you commenting the lines out like?:
```
#Section "ServerLayout"
#	Identifier	"Default Layout"
#	Screen		"Default Screen"
#	Inputdevice	"Synaptics Touchpad"
#EndSection
```
Every line, especially in the "ServerLayout".

You are sure the xorg.conf wasn't already there, say with video sections?  It would be if you were using the nVidia proprietary drivers for example.

---

### Post by higashi on 2011-08-06
Yes, I made sure to comment out every line.
I'm not 100% sure that the xorg.conf weasn't already there, but when I was configuring it, it was blank (so I assumed that it was just created). 

I don't quite understand what you said about the touchpad and I don't know how I'd fix that

thanks for all the help so far

---

### Post by Favux on 2011-08-06
Sure.  That should have worked.

You shouldn't need to fix the touchpad.  It should be auto-configured in xorg.conf.d, i.e. /usr/share/X11/xorg.conf.d.  It shouldn't matter that an entry was removed from the xorg.conf.

I don't really see what else would be causing a problem.  The linked file shouldn't hurt.  You shouldn't have been able to compile a wacom.ko because linuxwacom won't compile on a Xserver 1.7 (Lucid) much less the 1.10 in Natty.  Did you do the prebuilt instructions in step 15?

Did you install a wacom.rules?  It's called 50-xserver-xorg-input-wacom.rules in /etc/udev/rules.d in the HOWTO.  Maybe that link is to old SYSFS rules instead of Ron's newer ATTRS rules.  The file is now called 69-xserver-xorg-input-wacom.rules and is in /lib/udev/rules.d.  So check with:
```
ls /etc/udev/rules.d
```

---

### Post by higashi on 2011-08-06
```
$ ls /etc/udev/rules.d
50-xserver-xorg-input-wacom.rules  70-persistent-net.rules
70-persistent-cd.rules             README
```

---

### Post by Favux on 2011-08-06
Alright, we definitely want to remove that, so:
```
sudo rm /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules

```
then reboot.

---

### Post by higashi on 2011-08-06
ok, my trackpad is working again, but trying to regular boot still just gives me a blank screen

---

### Post by Favux on 2011-08-06
It sounds like you may have a problem with the video driver.  What video chipset do you have?  Is it nvidia?
```
lspci | grep VGA
```

---

### Post by higashi on 2011-08-06
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

---

### Post by Favux on 2011-08-06
I'm stumped.  Don't know what's wrong.  Not sure what you might have broke.  As far as I know an Intel integrated graphics is supported in Natty.  You can google it and see if something turns up.

Do you have one of those dual GPU setups with an integrated and then a standalone video card?  What kind of desktop or laptop is it?

I suppose you could try *nomodeset* on the kernel line.  When it boots up and you've selected the regular kernel line hit e to edit and add *nomodeset* to the *quiet splash* stuff.

And by the way what is the Wacom tablet you were trying to get working?  The model is on the bottom and the product ID is in the Wacom line in the output of *lsusb*.  Just post the whole line.

---

### Post by higashi on 2011-08-06
I have a Gateway Nv7915u laptop.
Is there any way to just reverse everything I did? just uninstall and delete things?

The tablet is still working the same (still no pressure sensitivity)

Anyway, your help is much appreciated :)

---

### Post by higashi on 2011-08-06
I'm using a Gateway NV7915u laptop and a Wacom Bamboo Fun tablet.
Is there any way to reverse the things I did? i.e. uninstall/delete things that were installed when I followed the guide ?

Thanks for all your help! :)

---

### Post by Favux on 2011-08-06
OK, but I need to know which Bamboo Fun.  Is it one of the new touch models with touch?  Model number on the back of the tablet and *lusb* in a terminal.

Well we got rid of the wacom.rules and essentially the xorg.conf.

Let's check if I'm wrong and if the pixman links are messing things up.  Look in /usr/include for files with pixman in the name.  What are their names?  If they are link files they have an arrow in the right lower corner.

Also did you do this step?
17.

sudo apt-get remove wacom-tools xserver-xorg-input-wacom -y
sudo apt-get install wacom-tools xserver-xorg-input-wacom -y

Because that would have removed xserver-xorg-input-all which might be the problem.  Check in Synaptic Package Manager that it or xserver-xorg-input-wacom is installed.  If not install either one and it will automatically install the other.  Ignore wacom-tools, it no longer exists.

---

### Post by higashi on 2011-08-07
The model is CTE-450
I didn't do any steps after 13, but I'm not really concerned about getting my tablet to work anymore, I'd just like to be able to regular boot :\

---

### Post by Favux on 2011-08-07
> I didn't do any steps after 13
Good to know, helps narrow things down.

In addition to the pixman stuff please post your xorg.conf (the complete contents) as is.  Also enter *uname -r* in a terminal and using your kernel version look in:
```
/lib/modules/`uname -r`/kernel/drivers/input/tablet
```
for the wacom.ko.  Right click on that and in Properties check the date.

By the way your Bamboo should have worked out of the box in Natty!

---

### Post by higashi on 2011-08-07
xorg.conf:
```
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#	Option		"USB"		"on"
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"pad"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"pad"
#	Option		"USB"		"on"
#EndSection

#Section "ServerLayout"
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
#	InputDevice	"pad"
#	Identifier	"Default Layout"
#	Screen		"Default Screen"
#	Inputdevice	"Synaptics Touchpad"
#EndSection
```

wacom.ko was last modified July 14, 2011

---

### Post by Favux on 2011-08-07
> wacom.ko was last modified July 14, 2011 
And that's when you installed Natty I suppose.

OK, the xorg.conf was useful because there are still some lines not commented out.  Not sure if they're causing a problem but should comment them out anyway.  The two Option usb lines:
```
	Option		"USB"		"on"

```
in eraser and cursor change to:
```
#	Option		"USB"		"on"

```
Use:
```
gksudo gedit /etc/X11/xorg.conf
```
Save and reboot.

---

### Post by higashi on 2011-08-07
Alright, we're making progress :0
I'm now able to regular boot, but it took longer than usual to boot up. Also my theme has been reset to something really ugly (this happened to me once before and I fixed it with Gnome-tweak, but that doesn't seem to be working this time around)

EDIT: rebooting fixed the theme problem (aside from some small imperfections, but I'm sure I can fix those with gnome-tweak), but it's still taking longer than it used to to boot up.

---

### Post by Favux on 2011-08-07
Outstanding!  :)

So commenting out the USB lines was the final bit to tip it over into booting with the Xorg Intel video drivers.  Great.

As you've seen sometimes rebooting a few times will shake things out a little, so always a good idea.

We've reversed just about everything.  From the instructions on the HOWTO you would have made a back up copy of your xorg.conf in the new *wacom* directory/folder you made in your /home/yourusername/ directory.  Check if there is an xorg.conf in there and post it.  That's just in case it somehow wasn't blank when you started and there might be something we should add back in.

Otherwise I think the only thing left is the pixman deal.  Did you check on that?  I don't have an comparable pixman libraries that I see in Natty so a link pointing to a non-existent library might slow boot down.

Also are you now interested in investigating why your Bamboo doesn't work?

---

### Post by higashi on 2011-08-07
the xorg.conf in my home folder:
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "ServerLayout"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

I haven't the slightest clue what pixman is, nor what to do with it :\

I'll Google a little more on how to get my pressure sensitivity working and then maybe start a different thread if I can't find anything.

Thanks again for all the help!

---

### Post by Favux on 2011-08-07
Nothing to see in the xorg.conf.  You can delete the wacom folder and its contents if you want to.

I talked about pixman a few posts back.  I just wanted you to use Nautilus to navigate the the directory the pixman links were in and see if they were there, i.e. what was there.

No need to google.  Wacom stuff is something I know a little about.  :)  That's why I originally answered your post.

For the Bamboo enter in a terminal and post the outputs of the following commands:
```
xinput list
and
xsetwacom list
```

---

### Post by higashi on 2011-08-07
```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Video WebCam                            	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
```

```
 $ xsetwacom list
SynPS/2 Synaptics TouchPad touch 
```

It's possible that my pressure sensitivity is in fact working. The only thing I know to test it on would be GIMP. The last time I tried to set up my tablet with pressure sensitivity and everything was probably before natty. This time around, I noticed that I didn't have the same options in the dropdown menu when editing the input devices.
This time around, the drop down box only gives me
-Virtual core XTEST pointer (disabled)
-SynPS/2 Synaptics TouchPad (disabled)

---

### Post by Favux on 2011-08-07
Right, we're not seeing your tablet at all in the xinput or xsetwacom lists.  So first step is to see if your wacom.ko is auto-loading.  Enter in a terminal:
```
dmesg | grep [Ww]acom
```
and post the output

---

### Post by higashi on 2011-08-07
oh my. I just realised that my tablet wasn't plugged in for that last post. Everything is working fine now... but it definitely wasn't working before I messed everything up (it wasn't detected at all before, even when plugged in lol)

Okay, everything's working fine now.
Thanks again for all the help! :)

---

### Post by Favux on 2011-08-07
Sure.  Glad it's all working now!  :)

---

