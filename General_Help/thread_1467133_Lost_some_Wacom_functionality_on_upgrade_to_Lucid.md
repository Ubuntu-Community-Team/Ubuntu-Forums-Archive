---
title: "Lost some Wacom functionality on upgrade to Lucid"
date: 2010-04-30
forum: General Help
---

### Post by Dave M G on 2010-04-30
Ubuntu Users,

As always, when I upgraded Ubuntu, I had problems with Wacom. This happens every upgrade, so it is not at all a surprise.

This time it wasn't quite as bad as others. I can use the Wacom device still, but it is stuck in "absolute" mode, when what I want is "relative" mode.

I used to be able to switch between absolute and relative mode, which was handy for using graphics programs, by using the following commands:

```
*(to switch to "relative" mode)*
xsetwacom set stylus mode relative; xsetwacom set stylus twinview none

*(to switch to "absolute" mode)*
xsetwacom set stylus mode absolute; xsetwacom set stylus twinview horizontal ScreenNo 0
```

If I try to run them in Lucid, however, I get this response:

```
Cannot find device 'stylus'.
```

I looked on the net, but the most information I could find was that I need to edit my 10-wacom.conf file, but I could not find any instructions on what syntax to use.

This is the content of my /usr/lib/X11/xorg.conf.d/10-wacom.conf file:

```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
       Option "Button2" "3"
       Option "Button3" "2"
EndSection
```

How do I get relative mode back, and get the switching commands to work?

Thank you for any advice.

---

### Post by Favux on 2010-04-30
Dave M G,

Unless you put the Wacom sections back into xorg.conf and use the section Identifiers like "stylus" and "eraser" etc. 'xinput --list' will not return stylus, or eraser.  In other words instead of the old linuxwacom device names you'll see longer, more descriptive device names, something like "Bamboo 5x6".  So you want the output of 'xinput --list'.  Say then:

stylus = "Device Name"

Then in the xsetwacom command use:
```
xsetwacom set "Device Name" mode relative; xsetwacom set "Device Name" twinview none
```
with the quotes.  I've also seen people use the ID #.  Since wacomcpl hasn't been split out of linuxwacom yet and transposed to xf86-input-wacom it isn't available.  So you need to set up your own script, instead of .xinitrc, call it say .xsetwacom.sh.  Then set it to autostart.  Or you could set scripts up with a launcher too.

---

### Post by Dave M G on 2010-05-01
Favux,

Thank you for replying.

I was able to get the exact identity of my Wacom device using the command "xinput --list", which gave me the following results:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ATEN UC-10KM V1.3.124                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Dexin Corp. LASER Mouse                 	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 6x8 eraser              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 6x8 cursor              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 6x8 pad                 	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 6x8                     	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; ATEN UC-10KM V1.3.124                   	id=8	[slave  keyboard (3)]
```

Then I was able to switch to "relative" mode with the following command:

```
xsetwacom set 14 mode relative; xsetwacom set 14 twinview none
```

So far so good.

However, I was a little confused by your last instruction to set up a script of my own.

Do you mean that there's no way to simply configure Wacom's settings file (10-wacom.conf) to make the device default to "relative" mode?

The reason I ask is because I was able to set the order of the buttons in that file by using the following code:

```
Option "Button2" "3"
Option "Button3" "2"

```

So I'm a little surprised something similar can't be done for other options.

---

### Post by Favux on 2010-05-01
No, I didn't mean to imply that.  You can use 'Option "Mode" "Relative"|"Absolute"' in xorg.conf.d if you want.  But if you want to set up a launcher to toggle between Relative and Absolute you need a xsetwacom script.  It just depends on how you want things setup, that's all I was trying to say.

---

### Post by Dave M G on 2010-05-03
Thank you for that.

I don't need a launcher to present options every time I log in, sorry if I was unclear.

What I want is for my Wacom to be relative mode when I boot up or log in. The command line toggles are for when I need to do some graphics work.

So thank you for telling me how to set the options in the configuration file. I'm basically set up the way I want now.

I'd like to go just a little further, though. Set up the speed of the cursor and that sort of thing.

Is there a place that has a definitive list of the options to use in the conf file?

---

### Post by Favux on 2010-05-03
Hi Dave M G,

Yes the LWP's HOWTO.

5.1 - Adding the InputDevices:  [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

9.0 - Command Line Configuration Interface (xsetwacom):  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

---

### Post by Dave M G on 2010-05-04
Favux,

Thank you for all your help!

I have my Wacom working as hoped now.

---

