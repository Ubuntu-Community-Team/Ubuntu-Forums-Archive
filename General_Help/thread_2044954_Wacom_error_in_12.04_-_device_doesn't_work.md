---
title: "Wacom error in 12.04 - device doesn't work"
date: 2012-08-20
forum: General Help
---

### Post by arsenic23 on 2012-08-20
Okay.  I have 12.04 installed and am using xfce (although I don't think that is relevant).

This morning I pulled my tablet out of its hole and to my surprise discovered that it wasn't working.  Looking in the mouse and tablet properties (xfce) I see that it is detected.  It lights up green like normal when the pen contacts the surface.  Okay.

So I took a look at my xorg.conf.  Well there really isn't anything there, and I'm pretty sure that is how it is supposed to be anymore.  [COLOR="Silver"]( Aw the days of manual typing out huge xorg.conf. )[/COLOR]

Then I greped through /var/log/Xorg.0.log and discovered something interesting.  I have about 3000 instances of:```
[   506.306] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
```

Google doesn't seem to turn up anything useful for this error message.  I'm completely at a loss.

**xorg.conf**:
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection
```

**Xorg.0.log** (Lines containing [wW]acom ; just imagine that last error stretching down about 2990 more times.):
```
[     8.447] (II) config/udev: Adding input device Wacom Intuos2 4x5 (/dev/input/event10)
[     8.447] (**) Wacom Intuos2 4x5: Applying InputClass "evdev tablet catchall"
[     8.447] (**) Wacom Intuos2 4x5: Applying InputClass "Wacom class"
[     8.447] (II) LoadModule: "wacom"
[     8.447] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     8.447] (II) Module wacom: vendor="X.Org Foundation"
[     8.447] (II) Using input driver 'wacom' for 'Wacom Intuos2 4x5'
[     8.447] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     8.447] (**) Wacom Intuos2 4x5: always reports core events
[     8.447] (II) Wacom Intuos2 4x5: type not specified, assuming 'stylus'.
[     8.447] (II) Wacom Intuos2 4x5: other types will be automatically added.
[     8.447] (--) Wacom Intuos2 4x5 stylus: using pressure threshold of 27 for button 1
[     8.447] (--) Wacom Intuos2 4x5 stylus: Wacom USB Intuos2 tablet maxX=12700 maxY=10600 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[     8.447] (II) Wacom Intuos2 4x5 stylus: hotplugging dependent devices.
[     8.447] (EE) Wacom Intuos2 4x5 stylus: Invalid type 'touch' for this device.
[     8.447] (EE) Wacom Intuos2 4x5 stylus: Invalid type 'pad' for this device.
[     8.447] (II) Wacom Intuos2 4x5 stylus: hotplugging completed.
[     8.448] (II) XINPUT: Adding extended input device "Wacom Intuos2 4x5 stylus" (type: STYLUS, id 8)
[     8.448] (**) Wacom Intuos2 4x5 stylus: (accel) keeping acceleration scheme 1
[     8.448] (**) Wacom Intuos2 4x5 stylus: (accel) acceleration profile 0
[     8.448] (**) Wacom Intuos2 4x5 stylus: (accel) acceleration factor: 2.000
[     8.448] (**) Wacom Intuos2 4x5 stylus: (accel) acceleration threshold: 4
[     8.448] (II) config/udev: Adding input device Wacom Intuos2 4x5 (/dev/input/mouse0)
[     8.460] (**) Wacom Intuos2 4x5 eraser: Applying InputClass "evdev tablet catchall"
[     8.460] (**) Wacom Intuos2 4x5 eraser: Applying InputClass "Wacom class"
[     8.460] (II) Using input driver 'wacom' for 'Wacom Intuos2 4x5 eraser'
[     8.460] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     8.460] (**) Wacom Intuos2 4x5 eraser: always reports core events
[     8.460] (--) Wacom Intuos2 4x5 eraser: Wacom USB Intuos2 tablet maxX=12700 maxY=10600 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[     8.464] (II) XINPUT: Adding extended input device "Wacom Intuos2 4x5 eraser" (type: ERASER, id 13)
[     8.464] (**) Wacom Intuos2 4x5 eraser: (accel) keeping acceleration scheme 1
[     8.464] (**) Wacom Intuos2 4x5 eraser: (accel) acceleration profile 0
[     8.464] (**) Wacom Intuos2 4x5 eraser: (accel) acceleration factor: 2.000
[     8.464] (**) Wacom Intuos2 4x5 eraser: (accel) acceleration threshold: 4
[     8.464] (**) Wacom Intuos2 4x5 cursor: Applying InputClass "evdev tablet catchall"
[     8.464] (**) Wacom Intuos2 4x5 cursor: Applying InputClass "Wacom class"
[     8.464] (II) Using input driver 'wacom' for 'Wacom Intuos2 4x5 cursor'
[     8.464] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     8.464] (**) Wacom Intuos2 4x5 cursor: always reports core events
[     8.464] (--) Wacom Intuos2 4x5 cursor: Wacom USB Intuos2 tablet maxX=12700 maxY=10600 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[     8.464] (II) XINPUT: Adding extended input device "Wacom Intuos2 4x5 cursor" (type: CURSOR, id 14)
[     8.464] (**) Wacom Intuos2 4x5 cursor: (accel) keeping acceleration scheme 1
[     8.464] (**) Wacom Intuos2 4x5 cursor: (accel) acceleration profile 0
[     8.464] (**) Wacom Intuos2 4x5 cursor: (accel) acceleration factor: 2.000
[     8.464] (**) Wacom Intuos2 4x5 cursor: (accel) acceleration threshold: 4
[   506.234] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.246] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.254] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.266] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.274] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.286] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.294] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.306] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.314] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.326] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.334] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.346] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.354] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.366] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
[   506.374] (EE) Wacom Intuos2 4x5 cursor: usbParse: Ignoring event from invalid serial 0
```

[COLOR="DarkRed"]**EDIT**[/COLOR]:

All the regular wacom checks work out and this seem okay, I think.
**xinput list**:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 4x5 stylus                	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 4x5 eraser                	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 4x5 cursor                	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; LOGITECH G110 G-keys                    	id=9	[slave  keyboard (3)]
    &#8627; Gaming Keyboard G110                    	id=10	[slave  keyboard (3)]
    &#8627; Gaming Keyboard G110                    	id=11	[slave  keyboard (3)]
```

[COLOR="darkred"]**EDIT**[/COLOR]:
I found this old thread: [http://ubuntuforums.org/showthread.php?t=1889282](http://ubuntuforums.org/showthread.php?t=1889282)
Seems to be the same problem, but no solution in sight.

---

### Post by Favux on 2012-08-20
Hi arsenic23,

Looks like the Intuos2's are running into this function in the wcmUSB.c file in xf86-input-wacom/src:
```

	if ((event->type == EV_MSC) && (event->code == MSC_SERIAL))
	{
		/* we don't report serial numbers for some tools
		 * but we never report a serial number with a value of 0 */
		if (event->value == 0)
		{
			xf86Msg(X_ERROR, "%s: usbParse: Ignoring event from invalid serial 0\n",
				pInfo->name);
			goto skipEvent;
		}

		/* save the serial number so we can look up the channel number later */
		private->wcmLastToolSerial = event->value;

		return;

	} else if ((event->type == EV_SYN) && (event->code == SYN_REPORT))

```
Apparently for some reason the serial number for the Intous2 cursor is being reported as zero which is causing the problem.

So does your tablet actually have a cursor/puck/tablet mouse?  If so what type?

We could try setting up a custon .conf file and tell the wacom X driver to ignore the cursor and see if that works.  Or as another temporary work around that might work comment out the function and recompile xf86-input-wacom until we figure out what's wrong.
```

/* temporary work around for Intuous2 cursor
	if ((event->type == EV_MSC) && (event->code == MSC_SERIAL))
	{
		/* we don't report serial numbers for some tools
		 * but we never report a serial number with a value of 0 */
		if (event->value == 0)
		{
			xf86Msg(X_ERROR, "%s: usbParse: Ignoring event from invalid serial 0\n",
				pInfo->name);
			goto skipEvent;
		}

		/* save the serial number so we can look up the channel number later */
		private->wcmLastToolSerial = event->value;

		return;

	} else if ((event->type == EV_SYN) && (event->code == SYN_REPORT)) */

	if ((event->type == EV_SYN) && (event->code == SYN_REPORT))

```
Then either way you should report the problem, and the fact that it affects multiple Intuos2's to linuxwacom-discuss:  [http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-discuss)  That's the quickest way to get a developer to take a look at the bug.

---

### Post by arsenic23 on 2012-08-20
> **Favux said:**
> So does your tablet actually have a cursor/puck/tablet mouse? If so what type?

Ahh... mmmm....  It came with one.  I don't have it, I don't use it.  It is more then likely packed away someplace.  Anyway I don't use it.  I just use the pen.

I think it was just a standard two button one wheel mouse.  I don't think it even had a middle click.  I got this guy when the Intuos2s first came out and haven't used the mouse since day one.

I'm completely lost on this.  The last time I was familiar with xorg was really during Breezy.  It is so very different now.  Also I have a poor memory.

---

### Post by Favux on 2012-08-20
> I think it was just a standard two button one wheel mouse. I don't think it even had a middle click.
It didn't have a lens with a cross hair did it?  If not my guess is it is the:
```
[0x094]
# Intuos and Intuos2
Name=4D Mouse
Type=Puck
HasLens=False
Buttons=5
```
That's from the libwacom.stylus file in libwacom/data.  Is it suppose to connect to the tablet with a usb cord?  Maybe that's the problem and xf86-input-wacom doesn't handle it correctly when it isn't connnected?  That seems hard to believe though, that it wouldn't handle that use case.

Now days the xorg.conf often isn't even present.  If it is you usually only see video driver stuff in it.  Either udev automatically handles configuration now or for usb devices that need configuration the xorg.conf.d in /usr/share/X11 is used so that the usb device has hot plugging.

Let's try a custom .conf to block the cursor from the driver and see where that gets us.  Check if you have the directory /etc/X11/xorg.conf.d, which is where the user adds custom options.  If not create it with:
```
sudo mkdir /etc/X11/xorg.conf.d
```
Then create the .conf with:
```
gksudo gedit /etc/X11/xorg.conf.d/52-wacom.conf
```
Then for the contents add:
```
Section "InputClass"
	Identifier "Intuous2 cursor ignore"
	MatchDriver "wacom"
	MatchProduct "cursor"
	# Apply custom Options to this device below.
	Option "Ignore" "on"
EndSection

```
Save and restart.

We're basically following this:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)

---

### Post by arsenic23 on 2012-08-20
Nope, no go.
I can see that it took here:
```
[     8.274] (**) Wacom Intuos2 4x5 eraser: Applying InputClass "evdev tablet catchall"
[     8.274] (**) Wacom Intuos2 4x5 eraser: Applying InputClass "Wacom class"
[     8.274] (II) Using input driver 'wacom' for 'Wacom Intuos2 4x5 eraser'
[     8.274] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     8.274] (**) Wacom Intuos2 4x5 eraser: always reports core events
[     8.274] (**) Option "Device" "/dev/input/event11"
[     8.274] (**) Option "Type" "eraser"
[     8.274] (--) Wacom Intuos2 4x5 eraser: Wacom USB Intuos2 tablet maxX=12700 maxY=10600 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[     8.276] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input11/event11"
[     8.276] (II) XINPUT: Adding extended input device "Wacom Intuos2 4x5 eraser" (type: ERASER, id 13)
[     8.276] (**) Wacom Intuos2 4x5 eraser: (accel) keeping acceleration scheme 1
[     8.276] (**) Wacom Intuos2 4x5 eraser: (accel) acceleration profile 0
[     8.276] (**) Wacom Intuos2 4x5 eraser: (accel) acceleration factor: 2.000
[     8.276] (**) Wacom Intuos2 4x5 eraser: (accel) acceleration threshold: 4
[     8.276] (**) Wacom Intuos2 4x5 cursor: Ignoring device from InputClass "Intuous2 cursor ignore"

...

[   186.224] (EE) Wacom Intuos2 4x5 eraser: usbParse: Ignoring event from invalid serial 0
```

But yeah, I'm still making a couple hundred of them every time I pass my pen over the surface of the tablet.  Now it just says eraser, so I Imagine it will do it no matter how many inputs I disable.

I tried making an old style xorg.conf, just to see, and all I did was render X unable to start until I restored the file.

---

### Post by Favux on 2012-08-20
>  Now it just says eraser
Alright so it isn't a cursor specific problem, the code is handling the Intuous2 events wrong it looks like.

So we can either try commenting it out and recompiling or just go straight to linuxwacom-discuss.  Your choice.

---

### Post by arsenic23 on 2012-08-20
Oh man.  It's been a long time since I compiled anything and that was never anything important.  

Well, if you are willing to waste time helping me out, I'm willing to try it.

I downloaded the source through apt-get, but I will admit I'm a bit ignorant on some things here.  I have a general idea what the .diff file is for, but no idea how to use it.  

Also, even if we comment out that section will [COLOR="DimGray"](common->wcmProtocolLevel == WCM_PROTOCOL_GENERIC)[/COLOR] evaluate as True in [COLOR="dimgray"]usbChooseChannel[/COLOR]?  I'm pretty sure that is what needs to happen - I think - maybe.  Reading the comments kind of gives me that idea.  I'm sure(mostly) that my tablet falls under Generic Protocol devices as it has never been able to handle more then one pen/mouse/etc at a time.

I installed build-essentials and some other ****, but I remember using makedeb (or something) when I used to compile software, to make it easier to remove if I broke something.  I don't see that so I'm thinking it has depreciated or I've forgotten something.

---

### Post by Favux on 2012-08-20
> Also, even if we comment out that section will (common->wcmProtocolLevel == WCM_PROTOCOL_GENERIC) evaluate as True in usbChooseChannel? I'm pretty sure that is what needs to happen - I think - maybe. Reading the comments kind of gives me that idea. I'm sure(mostly) that my tablet falls under Generic Protocol devices as it has never been able to handle more then one pen/mouse/etc at a time.

Well I'm no developer so...  But an Intuous2 is suppose to be a protocol 5 device:
```
common->wcmProtocolLevel = WCM_PROTOCOL_5
```
and the Intuos1 and 2 are suppose to be able to handle two devices on the tablet at the same time.  Allegedly.

For compiling (I'd suggest cloning the git repository) see either of these HOW TOs:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  or  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

Unfortunately we're not allowed to update them anymore so they're already getting dated and for Precise you need a patch in post #1034:  [http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034](http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034)

---

### Post by arsenic23 on 2012-08-20
> **Favux said:**
> and the Intuos1 and 2 are suppose to be able to handle two devices on the tablet at the same time. Allegedly.

hmmm...  Thats a surprise.  Well thanks for the help.  I'll mess with it tomorrow.

---

### Post by Favux on 2012-08-20
OK.  And if you still wanted to try an xorg.conf we could do that too.

---

### Post by arsenic23 on 2012-08-21
I don't have the time to play with this today like I thought I would but I tried to compile xf86-input-wacom last night.  Didn't even get started.  For some reason the patch wouldn't take.  It just sat there, doing nothing, using no CPU or anything.  I left it sit there for 20 minutes.  Then I ran it again with --verbose.  Nothing.

Thoughts anyone?  [COLOR="Gray"]( And now I'm off to work. )[/COLOR]

---

### Post by arsenic23 on 2012-08-22
I was looking around for other people having intuos2 problems and while I found a bunch of Fedora core users also out in the cold with their intuos2s I also found this thread:
**[http://ubuntuforums.org/showthread.php?t=2018700&page=2](http://ubuntuforums.org/showthread.php?t=2018700&page=2)**

So I tried disabling the drivers on boot, and what would you know?  Loading it manually the same way as that fellow got my tablet working.  It's kinda of hack of a solution, but working it better then not working.  [COLOR="Silver"]( And I still never got that patch to work. )[/COLOR]

---

### Post by Favux on 2012-08-22
> Fedora core users also out in the cold with their intuos2s I also found this thread:
[http://ubuntuforums.org/showthread.php?t=2018700&page=2](http://ubuntuforums.org/showthread.php?t=2018700&page=2)

So I tried disabling the drivers on boot, and what would you know? Loading it manually the same way as that fellow got my tablet working. It's kinda of hack of a solution, but working it better then not working. 
That is just weird.
> So I tried disabling the drivers on boot, and what would you know? Loading it manually the same way as that fellow got my tablet working. It's kinda of hack of a solution, but working it better then not working. 
Thanks for updating with that information.

Given that we've got two users who can use the same work around and that it also affects Fedora (links would be appreciated) I'm going to post about this on linuxwacom-discuss and link to your LWP forum post.

I tested the patch and it works for me so I would need more details to figure out what's wrong.  There've only been 10 testers or so, so far, which means I've only got a 1 out of 10 no go.  Not to say the other 9 were succesful.  Maybe they just didn't post.

---

### Post by arsenic23 on 2012-08-23
> **Favux said:**
> (links would be appreciated)

I can't find them.  I looked.  Maybe I imagined them or they were old posts?  Sorry.  I remember reading two other people complaining about what appeared to be the same problem in Fedora.  I dunno.

---

### Post by Favux on 2012-08-31
Hi arsenic23,

Jason seems to think this is a Ubuntu specific problem that started after Maverick 10.10.  He's supplied a hack for input-wacom-0.14.0:  [https://github.com/jigpu/input-wacom/commit/30b145fa2703596c1f5c31e39f9084db7cedd670](https://github.com/jigpu/input-wacom/commit/30b145fa2703596c1f5c31e39f9084db7cedd670)  You can apply the patch to input-wacom and compile the wacom.ko.  In Precise don't forget to apply the build-against-frankenserver.patch also.

---

### Post by arsenic23 on 2012-09-01
Oh, thank you.  I'll play around with that next weekend.
Also I found those Fedora posts I thought were the same problem.  It was a case of similar problem several years ago and me missing the date.

Sorry.

---

### Post by Favux on 2012-09-01
Let me know how it goes.  When he gets time he says he'll try to figure the problem out.  That would be lucky because usually the LWP dev.s aren't interested in Distro specific issues figuring that's the Distro's problem.

I see I forgot to explain the build-against-frakenserver.patch is for xf86-input-wacom if you are updating that too:  [http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034](http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034)

---

