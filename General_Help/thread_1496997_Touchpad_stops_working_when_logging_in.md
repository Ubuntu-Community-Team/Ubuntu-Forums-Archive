---
title: "Touchpad stops working when logging in"
date: 2010-05-30
forum: General Help
---

### Post by border on 2010-05-30
I have an Hp Tx2 tablet with Lucid on and recently my touchpad siezed to work while resizing a large partition on an external usb hard disk (which I believe has nothing to do with it). The resizing took me a day or 2. Since then, every time I log in, my touchpad freezes. It works fine at the login screen. As far as I recall, I did not do any substantial updates or apt-get installs recently

When I cat /dev/input/mice it does give output, so I assume that it still works, there's just something in between, blocking my touchpad when logging in.

The driver is psmouse I figure (although I would think it's an usb touchpad), and if I remove the module and reload it, that does not make a difference.
I already tried blacklisting, and loading after logging in.

Anyone any input on how to debug/solve that?

thanks

One thing I can add is when plugging in a usb mouse, that one does work. But that doesn't change anything on behalve of my touchpad. So it seems they use a different driver

---

### Post by Ayuthia on 2010-05-31
Have you checked xinput --list to see if the touchpad is listed?  You might also check and see what /var/log/Xorg.0.log shows for the touchpad.  It could be that an xorg driver has not been assigned to the touchpad.

---

### Post by border on 2010-05-31
It is working when I'm at the login screen
So I guess the driver is loaded, but gets blocked by something while logging in. The question is by what and why?

xinput --list shows my touchpad

 Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Basic Optical Mouse           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=12	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                       	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=17	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]

and cat /var/log/Xorg.0.log | grep touchpad gives


(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
(--) SynPS/2 Synaptics TouchPad: touchpad found
(--) SynPS/2 Synaptics TouchPad: touchpad found

So I guess the synaptics driver loads fine and finds the touchpad also...

So that produces output as if it is working...

---

### Post by Ayuthia on 2010-05-31
> **border said:**
> 
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
(--) SynPS/2 Synaptics TouchPad: touchpad found
(--) SynPS/2 Synaptics TouchPad: touchpad found

So I guess the synaptics driver loads fine and finds the touchpad also...

So that produces output as if it is working...

From the information above, it looks like your touchpad is trying to use the evdev driver instead of synaptics.

Are you using xorg.conf.d?  If so, you can create 11-synaptics.conf and add the following:
```

Section "InputClass"
    Identifier "synaptics-all"
    Driver "synaptics"

    MatchIsTouchpad "on"
    MatchProduct    "SynPS/2 Synaptics TouchPad"
    Option "SHMConfig" "true"
    Option "SendCoreEvents" "true"
    Option "Emulate3Buttons" "true"
    Option "LeftEdge" "1700"
    Option "RightEdge" "5300"
    Option "TopEdge" "1700"
    Option "BottonEdge" "4200"
    Option "VertEdgeScroll" "true"
    Option "VertScrollDelta" "100"
    Option "TapButton1" "1"
EndSection

```
You might not need all of those options though.  I just have mine set that way because I grabbed it from my other laptop and have not tested what options are really needed.

I hope that helps.

---

### Post by border on 2010-06-01
I tried your solution, with the same result as before.
At the login screen everything works (keyboard, touchpad and touchscreen) and while logging in, my touchpad gets blocked and stops working.

I tried fiddling around with the xorg.conf.d settings and deleted everything I should not need, but that did not change anything, except for making me understand more what that's all about and how it works.

I booted to a root prompt and started the x server manually (startx) and then I have a working touchpad. At that moment I tried logging in as my user to start the x server from there, but it would not start.

So I'm thinking more in the area of some service which starts after logging in and blocks my touchpad. A service that does not get loaded if you startx from a root prompt. But I have no clue where to start looking.

thanks a lot for trying to help me already

---

### Post by Ayuthia on 2010-06-01
You might check /var/log/Xorg.0.log when you use startx and logging in normally to see if it is using a different driver.  If it is, then we need to see which rule is pulling in the driver.  The information should show in /var/log/Xorg.0.log.


EDIT:
By the way, do you have an evdev.conf file in /etc/X11/xorg.conf.d?  If so, can you post it?

---

### Post by border on 2010-06-01
this is my 05-evdev.conf file

#Section "InputClass"
#	Identifier "evdev pointer catchall"
#	MatchIsPointer "on"
#	MatchDevicePath "/dev/input/event*"
#	Driver "evdev"
#EndSection

Section "InputClass"
	Identifier "evdev keyboard catchall"
	MatchIsKeyboard "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

#Section "InputClass"
#	Identifier "evdev touchpad catchall"
#	MatchIsTouchpad "on"
#	MatchDevicePath "/dev/input/event*"
#	Driver "evdev"
#EndSection

#Section "InputClass"
#	Identifier "evdev tablet catchall"
#	MatchIsTablet "on"
#	MatchDevicePath "/dev/input/event*"
#	Driver "evdev"
#EndSection

Section "InputClass"
	Identifier "evdev touchscreen catchall"
	MatchIsTouchscreen "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

At the start, nothing was commented out
I tried to comment out the lines I don't need. First I commented out too much, which left me without the keyboard.

There's also a synaptics, a wacom and a vmmouse .conf file.
I guess that I don't need the vmmouse, just the synaptics (touchpad) and the wacom (for my touchscreen).

I'll look to the Xorg.0.log file in more detail when I get the chance.

---

### Post by border on 2010-06-01
the relevant sections in Xorg.0.log are these:


(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event14)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event14"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)


They are exactly the same when logging in with my user, or when starting x from root. And still I don't have a working keypad as a user, but I have one as root.

So I guess we can look for the problem anywhere else?

How can I know which processes are started and which commands are executed when I log in?

cheers

---

### Post by border on 2010-06-01
This might seem very wierd (it is to me), but I was trying to fiddle around with bum, decided that it was not going to help, taken a look at gnome startup services and did not change anything at all and all of the sudden my touchpad works again!!!!

Even when I log out and back in, it does not freeze anymore. So I hope the problem is gone now.

Only now I'm probably never gonna know what caused the problem. I just remember mistakenly trying to add an empty startup service to the startup programs list found under system->preferences while looking there. I was trying to clean my touchscreen with a handkerchief and while doing it went crazy, clicking a few buttons.
But all it did was creating an empty startup service, and removing the error message and it did that a few times.
It does not explain anything. It does not seem sane. But it is the way it is.

I thought that one could understand everything that goes on in a linux system. Appearantly one cannot.

---

### Post by tobydeemer on 2010-06-21
After I started seeing these symptoms as well, noticed this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727)

Seems there's a larger matter going on. For me, as temp fix, I had to reset teh gconf-tool switch. Our saga continues...

---

### Post by border on 2010-06-21
So far, I have not been troubled by that bug anymore.
I do not recall having run the update-manager prior. I had a feeling it just came and it just went.
Seems everyone being affected by the bug has a hardware button to disable the touchpad...

---

### Post by lev_davidovich on 2010-06-21
Hi,

I have the same problem. Touchpad works before logging in, then it must get switched off by something. I'm an inexperienced user running 10.04. The touchpad worked fine one day, then didn't the next. The only thing I remember doing was messing around trying to get the Open Office Zotero plugin to work - this also involved messing around with Java plugins.

Any help much appreciated!

---

### Post by Pikachuu on 2010-08-17
Apologies for necromancing, but I have encountered this problem as well, except that when I press the toggle touchpad button, my input shuts down completely, save for being able to swap workspaces and adjusting the brightness using fn+Function keys on my HP touchsmart tx2.

EDIT: It works on my other account for general use. Strange.

---

### Post by Austin25 on 2010-09-06
I have had the same problem as well, It's been off and on. Seems switching ttys, hitting menus, or restarting sometimes make it work. I hope this gets fixed, as it's very annoying. Also, sometimes it affects the keyboard, as well as the the menu in the top panel.

---

### Post by Austin25 on 2010-09-13
Still does it. Seems to be triggered by the "turn of touchpad button." By it not working, I mean it won't come back when I press it again.

---

### Post by JamesSmith on 2010-09-25
Hi

This same problem is troubling me, except that the touchpad does not work at any stage of my Aspire One running (ie not even pre-login).  It all started about a week ago when the netbook randomly locked up. After rebooting, it hasn't worked since.  Switching any of the Fn functions makes no difference to any input functionality either,  I can use a usb mouse, and here are the xinput and X.org.0.log outputs:

james@AspireOne:~$ xinput --list

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

james@AspireOne:~$ cat /var/log/Xorg.0.log | grep touchpad

(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
(--) SynPS/2 Synaptics TouchPad: touchpad found
(--) SynPS/2 Synaptics TouchPad: touchpad found

If anyone can help me with this I'd be most grateful.  I'm a bit of a novice when it comes to the inner workings of the Linux system.

Thanks in advance. James

---

### Post by JamesSmith on 2010-09-25
I apologise for my pre-emptive post, but it appreas to have fixed itself.  I booted into a Live Xubuntu session from a USB stick.  At first the touchpad was not working, but I was able to turn it on using the Fn+F7 combo and now, back in Ubuntu it is working fine.

Hmm.

---

### Post by Austin25 on 2010-10-04
> **JamesSmith said:**
> I apologise for my pre-emptive post, but it appreas to have fixed itself.  I booted into a Live Xubuntu session from a USB stick.  At first the touchpad was not working, but I was able to turn it on using the Fn+F7 combo and now, back in Ubuntu it is working fine.

Hmm.
Yeah, it does that. It randomly stops working, then randomly starts working again.

---

### Post by Austin25 on 2010-10-04
Probably a driver bug. Anyone have a patch?

---

### Post by Austin25 on 2010-11-19
Happened again recently.

---

### Post by Austin25 on 2010-11-21
Still does it. It's happening right now. I can provide data. Please, help. PLEASE!!!

---

### Post by tobydeemer on 2010-12-09
This just happened again for me today, after several months of no symptoms. This time, using gconf-editor, this key: .gconf/desktop/gnome/peripherals/touchpad, my entry for "touchpad enabled" was unchecked for no reason.

I checked it, and the touchpad sprang to life, no log out, reboot, or anything.

---

### Post by Austin25 on 2010-12-31
I can confirm this.

---

