---
title: "Wacom Intuos4 on 9.10x64"
date: 2010-02-06
forum: General Help
---

### Post by Sumanitu Taka Nagi on 2010-02-06
Hey there...I was hoping I could get some assistance with my graphics tablet.

I'm already tried working through the Ubuntu Wacom Documentaion and the documentation provided at the Linux Wacom Project website.

And to be honest, sometimes it gets hard to follow, especially the latter. I mean, I usually know enough with jsut having played with Ubuntu before to be able to follow directions, but when i come across problems or instructions that aren't applicable to me, then I don't know what to do. So I was helping if I could get someone to help guide me though it.

I'd really appreciate it...I want to get drawing, and this is one of the few things that's keeping windows on my hardrive...but if I can get it operable and very functional...well that may not last.

Anyways, yeah the tablet I've got is a Wacom Intuos4 and I'm running on Ubuntu 9.10 and the 64 bit edition, I've already isntalled Wacom-tools xserver-xorg-input-wacom available in synaptic My tablet used to at least operate whn i'd first plug it in, butt he mapping was all screwed up, I'm not sue how to explain it butt he best way i can put it is that I guess the scaling from the stylus on the tablet to the cursor and the screen seeme off, that's when i tried following those documentations...

Now it doesn't seem to even do that much...so if someone could me get my stylus and mouse and wahtnot working and mappinga nd functionally well I'd really appreciate it.

Thanks ahead of time.

---

### Post by Favux on 2010-02-06
Hi Sumanitu Taka Nagi,

What changes did you make?  Did you add Wacom stuff to xorg.conf?

What is the output of:
```
xinput --list
```
and
```
xsetwacom list
```
in a terminal?

---

### Post by Sumanitu Taka Nagi on 2010-02-07
Yeah I made changes to xorg.conf, but then I ended up removing them.

Results of xinput --list:

nagi@Wolf-Linux:~$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"UVC Camera (046d:09a1)"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Logitech Logitech USB Keyboard"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"PIXART USB OPTICAL MOUSE"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
nagi@Wolf-Linux:~$ 

And No Feed back on the second command...



nagi@Wolf-Linux:~$ xsetwacom list
nagi@Wolf-Linux:~$

---

### Post by Favux on 2010-02-07
Hi Sumanitu Taka Nagi,

OK, your Intuos4 isn't showing up on xinput.  Did you try to compile linuxwacom?  If so which version?

If not then in Synaptic tell it to reinstall wacom-tools xserver-xorg-input-wacom and reboot.

You may also have removed your wacom.fdi.  For a modified .fdi and how to setup wacomcpl see [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

---

### Post by Sumanitu Taka Nagi on 2010-02-07
I think I was getting ready to compile linuxwacom as instructed in the Wacom Linux Project documentation...I remember configuring it and then getting ready to make it and then i had a slew of errors and I was pretty stuck at that point :/

Do you still want me to go forth we reinstalling that package though?

The Version was linuxwacom.0.8.4-4

---

### Post by Favux on 2010-02-07
Alright, if you didn't do a 'sudo make install' you should be OK and can reinstall.

One other thing you might want to check after reinstalling the linuxwacom drivers, aside from the xinput command, is if the wacom.ko is auto-loading:
```
lsmod | grep wacom
```
Do that before messing with the .fdi.

---

### Post by Sumanitu Taka Nagi on 2010-02-07
Sorry I kinda did this out of order, I ran the command for checking if the wacom.ko file auto loaded after I did all that futzing with the fdi file x3

Hope I didn't screw anything up...

nagi@Wolf-Linux:~$ lsmod | grep wacom
wacom                  25992  0 
nagi@Wolf-Linux:~$ 


So far everything seems mostly going...just gotta screw around with the tracking settings I guess in the Wacomcpl until it feels better and i'm not dragging everything from one edge to the other just to move the cursor around hehe.

thanks a bunch

-hugs-

---

### Post by Sumanitu Taka Nagi on 2010-03-09
Okay, well I've had a minor problem and I 'thought' it was resolving tiself but ti hasn't been and I've been trying to ignore it but it's getting really annoying...

When I first boot up Ubuntu and log in my tablet seems to work fine, it's got all my preferences saved and the devices for ti are all working with their configurations set how I want....and then shortly after it seems like the configuration just spontaineously resets.

My buttons reset, sometimes my mouse stops working until I unplug it and plug it back in or switch to the stylus and switch back, and my tracking resets :/


Anyone have any ideas why this might be?

---

