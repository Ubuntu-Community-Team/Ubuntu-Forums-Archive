---
title: "Black dots on the screen"
date: 2009-09-24
forum: General Help
---

### Post by gillespiea on 2009-09-24
Hi everyone, before you say "your screen is broke", it's not. I have tested another screen and have the same issue. My issue is that up the top left of my screen i have black dots randomly scattered over the corner.

I am using compiz and emerald and i have tried turning a few things on and off to see if that is the problem and so far nothing is working. Has anyone else had this problem?
I'll attach a screen shot as it shows in that.

---

### Post by ninjapirate89 on 2009-09-24
Have you tried changing the background on the panel to see if it changes anything?

---

### Post by fcuk112 on 2009-09-24
had a similar issue with my gfx card, i fixed it by upping the voltage in the bios.  seemed to work for me.

on a side note, i am quite curious as to what you are using for your dock, and how do you get those applets in the top-right corner.

cheers.

---

### Post by gillespiea on 2009-09-24
using an old cairo-dock mate. 1.6.something
was the only one i could get working. the things up the top right are pasrt of it.

if the dots where something to do with the graphics card i wouldn't be able to take a screenshot of it. Its not just on the top panel, it comes down a bit too. can see it on the top left of firefox, or any other open window that is over there.

---

### Post by gillespiea on 2009-09-24
Thought i'd pop up another screeny
You can see what i'm talking about much better on here.

---

### Post by sideaway on 2009-09-24
I've never seen anything like it, the closest I can think that comes to is video artifacting. That's really odd. Does it happen with a live CD?

---

### Post by gillespiea on 2009-09-25
not too sure. i'll have a check.

---

### Post by trundlenut on 2009-09-25
I used to get something similar on an old desktop machine (with an old 2x AGP ATi card IIRC)  there would a pattern of squares in the top left hand corner about an inch square.  Strangely it would normally disappear if I let the screensaver come on and then went back to the desktop.  I assumed it was a driver problem, but I no longer use that machine so I never got around to sorting it out.

---

### Post by trundlenut on 2009-09-25
> **rikiquique said:**
> I can't see any black dots on either of your published screens and I've got my reading spec on! :)

There are at least 10 in the top left hand corner.  See the blown up bit attached.

---

### Post by trundlenut on 2009-09-25
They seem to have artifacts around them rather than just being stuck pixels, assuming it is a flat screen and not a good old CRT.

---

### Post by gillespiea on 2009-09-25
It is a TFT monitor, Its not the monitor as i checked by using another monitor. They are still there when i use the other one. Although it's looking like i'm going to have to do a reinstall as my ubuntu wont load now...just hangs on boot. Thanks everyone for looking at my problem but it seems it won't get solved.

---

### Post by gillespiea on 2009-09-25
Sorted!
After sorting the hanging on boot problem by using the recovery option in GRUB (just turns out i had mounted the hdd 22 times without checking it) i continued the boot and the dots have gone! must have been something to do with the hard drive then...strange but true eh?

Now how do i make this solved in the topic header?

---

### Post by gillespiea on 2009-09-25
nope never mind. the dots are back. any other sugestions? i dont fancy booting through the recovery option everytime i want to use my computer.

---

### Post by trundlenut on 2009-09-26
What make and model is your graphics card?

---

### Post by 3rdalbum on 2009-09-26
The screenshot shows the artifacts, so it's obviously not a monitor problem. I'm not even sure if it can be a video card problem if we can see it on a screenshot.

Does this occur when you're running a non-Linux operating system? What happens if you change /etc/X11/xorg.conf to use the "vesa" driver rather than your ordinary accelerated one?

---

### Post by gillespiea on 2009-09-26
i'm using 2x XFX GeForce 8800GS. but only using the one. If i run the live CD they are not there. as for changing the driver. i havn't checked yet but will try now, will try update the nvidia driver first though.

---

### Post by gillespiea on 2009-09-26
Thought I'd add what is in my my xorg.conf just to see if anyone knows if there is anything i should change there.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by gillespiea on 2009-09-26
Ok...the new driver made my pc break for some odd reason. so after spending a good half hour trying to get my xserver working correctly i finnaly got it back to the way it was (instead of 800x600 with no 3d) with the black dots still there...
What i did notice when the computer was using the generic driver was some odd distortion where the dots where and then some of the screen would be blacked out (round about where the dots are at the moment) untill i click on Applications, Places or System, but i had to click each one to clear the blacked out area. I thought it could be a malfunctioning "Widget" from Cairo-Dock but i cant find one there. I'll try upgrading it (with the probability that it will break on me again) and see what happens...although its still there when i close cairo-dock :S

---

### Post by trundlenut on 2009-09-26
Do the dots remain if you drop the resolution a bit?

I'm sure that my problem was at least partially related to the graphics card as I didn't have the problem when using the built in graphics chip, only when using the ATi card in the AGP socket.

---

### Post by utnubuuser on 2009-09-26
Used to get a similar issue on an old hp laptop. -- likewise, never found an acceptable solution. - the issue persisted across disrtibutions as well - ie debian, ubuntu etc

---

### Post by gillespiea on 2009-09-26
Installed a different driver, and the dots remained...the screen flickered after another hour of use...turned my compiz off by iteself then i relogged and the dots are gone... i'm sure they will return after i reboot though.

I have been using ubuntu 8.04 on this PC for ages now and never had this problem before. I was using the 64bit version before but went for the 32bit this time..but again i have used the 32bit before without any problems. A strange one this...

---

### Post by Clucky on 2011-03-22
I am having the same exact problems, however, I didn't notice it until I installed Compiz. I also have a Nvidia GeForce 8400gs, so it could also be the graphics chard. I suggest you try asking Compiz and seeing if they know anything about it.

---

### Post by dv_ on 2011-04-30
I seem to have solved the black dots issue. Apparently, the closed source nvidia drivers and natty's splash screen do not like each other, so I did two things:

1) in /boot/grub/grub.cfg , removed "splash" and "quiet" from the kernel command line
2) I deinstalled plymouth-theme-kubuntu-logo

---

### Post by kaziem on 2013-03-15
I am experiencing the exact same problem with Ubuntu 12.10. Who would've guessed after all this time that this hasn't been corrected :)

I have an NVidia 660GTX Titanium!

Anyone found a solution for this yet?

Thanks!

---

### Post by wildmanne39 on 2013-03-15
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

