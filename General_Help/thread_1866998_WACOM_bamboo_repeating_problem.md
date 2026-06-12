---
title: "WACOM bamboo repeating problem"
date: 2011-10-22
forum: General Help
---

### Post by AdrianPtchv on 2011-10-22
Well, here it goes again. Another upgrade and the same problem with the wacom tablet as usual.


The problem after every upgrade of the OS is that buttons 2 and 3 of the pen work when the pen is not in touch with the tablet. I want them to work only when the pen's tip touches the tablet.

I tried to edit 50-wacom.conf with the setting that worked for the previous upgrade and it didn't work. 

If someone has an idea, please share.

---

### Post by Favux on 2011-10-22
Hi AdrianPtchv,

If:
```
Option "TPCButton" "on"
```
doesn't work after the *Driver "wacom"* line in the relevant snippet does using xsetwacom work?
```
xsetwacom set "device name" TabletPCButton on
```
Where you get the stylus <device name> from *xinput list*.

---

### Post by AdrianPtchv on 2011-10-22
Hi,

I am not sure I understand your post, but that is what I have in /usr/share/X11/xorg.conf.d/50-wacom.conf:

```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "TPCButton" "on"
EndSection

## N-Trig Duosense Electromagnetic Digitizer
#Section "InputClass"
#	Identifier "Wacom N-Trig class"
#	MatchProduct "HID 1b96:0001|N-Trig Pen"
#	MatchDevicePath "/dev/input/event*"
#	Driver "wacom"
#	Option "Button2" "3"
#EndSection
```

The first part is according to your instructions from the previous Ubuntu update and it worked for it.
The commented part is what was there before my edit (and it didn't work).

---

### Post by AdrianPtchv on 2011-10-22
I tried to put ```
xsetwacom set "device name" TabletPCButton on
``` instead of ```
Option "TPCButton" "on"
``` and the result was that the desktop could not boot until I edited the file back.

---

### Post by Favux on 2011-10-22
xsetwacom commands are runtime, not static, commands.  So you just run them in a terminal and they apply right away, not in a .conf file.  The Option settings are static so they need to be in a .conf file or xorg.conf.

If you have a usb tablet then your Option in the usb snippet in 50-wacom.conf should have worked.  Let's figure out why it isn't working.

What release of Ubuntu are you in?  You can determine your version of the Wacom X driver by running this command in a terminal:
```
xsetwacom -V
```
Also let's look at the output of this command run in a terminal:
```
xinput list
```

---

### Post by AdrianPtchv on 2011-10-23
Hi,

I'm running the Ubuntu 11.10.
It is an USB tablet and that is the output of the two commands:```


~$ xsetwacom -V
0.11.0

~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo1 stylus                    	id=8	[slave  pointer  (2)]
&#9116;   &#8627; USB Multimedia Keyboard                 	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo1 eraser                    	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo1 cursor                    	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; USB Multimedia Keyboard
```

---

### Post by Favux on 2011-10-23
OK, so you have a Bamboo One.  I need to see the product ID for your tablet.  Enter *lsusb* in a terminal and post the Wacom line in the output.

What is the output of?
```
xinput list-props "Wacom Bamboo1 stylus"
```

---

### Post by Favux on 2011-10-23
Found the problem.  Should have realized it earlier.  The xsetwacom command should work.  Have you tried it in a terminal yet?

Anyway what is going on is that with Oneiric you have GNOME 3.2 which includes the first version of the Wacom Graphics Tablet applet in System Settings.  What the applet uses is new hooks added to the gnome-settings-daemon.  However this first version only uses some of the hooks already added.  One of the hooks it doesn't use yet is the tablet-pc-button key in the gnome-settings-daemon under wacom.

The gnome-settings-daemon overrides any static setting.  So your Option in 50-wacom.conf is being overridden by the setting in the gnome-settings-daemon.  In turn a xsetwacom (runtime) command would override that.

I just checked and by default apparently the tablet-pc-button key is set off.  So you need to check the box to turn it on.  Since the applet doesn't have that option yet you need to use dconf-editor.  You may need to install it first.

Then open dconf-editor and go to org.gnome.settings-daemon.peripherals.wacom and you'll see the key.  Check the box.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)

---

### Post by AdrianPtchv on 2011-10-29
That worked!
Thank you!

Let me see what I'll have to do for the next update :)

---

### Post by AdrianPtchv on 2012-05-12
Hi,

Another update and again the same problem.
The tablet controls are (again) governed by different setting file/daemon/whatever.... 

This time dconf-editor's tablet-pc-button checkbox is checked but no effect - it is still off from the system's point of view i.e. I have to do hover gestures in firefox etc.

Does anybody know what is it this time?
How should the wacom tablet be configured in this version of Ubuntu (the latest 12.04 lts) so the tpcbutton is on?

xsetwacom set Bamboo1 TabletPCButton on does the trick by the way....


Thanks in advance!

---

### Post by Favux on 2012-05-13
Hi AdrianPtchv,

I don't see the TabletPCButton key value in the gnome-settings-daemon for Wacom with dconf-editor either.  And as you would expect there is no setting for it in the GNOME Wacom Graphics Tablet applet in Systems Settings.  The question is did they deliberately remove it from the daemon, or is it still there but invisible?  Presumambly invisible due to a bug.

My BambooPT tablet defaults to TabletPCButton on behavior but when I query it I see:
```
~$ xsetwacom get 8 TabletPCButton
off

```
it is set to off by default despite behaving like it is on.  When I set it to on:
```
~$ xsetwacom set 8 TabletPCButton on
```
there doesn't appear to be any change in behavior.  If I query it again:
```
~$ xsetwacom get 8 TabletPCButton
on

```
So at least it is being "set" by xsetwacom.  Setting it back to off again works according to "get" but again with no behavior change.

So something is clearly broken.  In the gnome-settings-daemon?  I'll look around a bit.  Let me know if you find anything.

---

### Post by Favux on 2012-05-13
I looked at xf86-input-wacom and nothing jumped out at me as being something that would have broken TabletPCButton when going from 0.12.0 (Oneiric's default) to 0.14.0 (Precise's default).  So I poked around some more in gnome-settings-daemon with dconf-editor.  Sure enough it appears you can disable the Wacom component of it, gsdwacom.

With gsdwacom I think I found a temporary work around.  Using dconf-editor navigate to:
> org.gnome.settings-daemon.plugins.wacom.gsdwacom.active
Uncheck the box so it is no longer active.  Doing that, at least for me, made the xsetwacom set commands work.  Now I can change the TabletPCButton behavior again.  Of course this means you can't use any of the Wacom Graphics Tablet applet's other features.

So it does look like the bug is in the gnome-settings-daemon.


Edit:  Interestingly after I made gsdwacom inactive and changed TabletPCButton to off and then made gsdwacom active again I was able to change the behavior with xsetwacom thereafter.  The gsdwacom plugin no longer interferred with xsetwacom's TabletPCButton parameter.  Haven't yet checked to see what happens with a restart.

Edit2:  After a restart the ability of xsetwacom to change the behavior is preserved.  At least on my system.  I am able to set TabletPCButton on and off and produce the expected behavior; gsdwacom is no longer interferring.  I'm interested if the same is true for you.

---

### Post by AdrianPtchv on 2012-05-20
Hi,

Thanks for the help! I've actually did it differently - just set the command to be executed at every boot so it works as I want.
I'll try your way whenever I find some time for this.

If not, I am sure we'll talk again with regard to the same issue after the next update to a new version :)
(As it seems that every new version traditionally breaks the wacom settings.)

Again, thanks for the effort to help!

---

