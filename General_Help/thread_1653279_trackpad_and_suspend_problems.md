---
title: "trackpad and suspend problems"
date: 2010-12-26
forum: General Help
---

### Post by martank on 2010-12-26
Hey, I'm new to ubuntu, running it on my macbook (4,1). I'm getting mixed searches for previous problems, especially since most seem to span back to previous releases.

Mouse problem:
The mouse is not correctly responsive. It's shakey weather or not it acknowledges the input of my finger on the trackpad. It's hard to tell if it thinks it is "accidental input" or not enough pressure on the pad. It also likes to "run" along some sort of imaginary horizontal lines on the screen (elsewhere on the internet I've seen it described as a grid). I've read about people editing their xorg.conf and changing the input pressure and such, but with ubuntu 10.10 they've split the xorg.conf file up into several files. Any guidance?

Screen dimming/sleep problem:
My screen likes to randomly dim itself when I'm using it, or not follow my power consumption configuration. It's speradic as to what's going on here, so I don't know that I can correctly describe it yet. Also, my mouse doesn't work when the screen dims and I have to use the brightness+ key to rewake the desktop. No other button seems to work, or the mouse. I have a similar problem when opening/closing the laptop, too. Sometimes it awakes, but several times I've had to restart because I can't do anything. 

boot error:
I get this error message twice when booting, and then it continues and seems to be a nonissue, but I don't know what the error is for:

modprobe: Fatal: /lib/modules/2.6.35-24-generic .... somethingsomething

Any help would be greatly appreciated. My biggest qualm is the mouse, as it is seriously hindering my navigation abilities. Thanks!!

---

### Post by libssd on 2010-12-26
> **martank said:**
> Mouse problem:
The mouse is not correctly responsive. It's shakey weather or not it acknowledges the input of my finger on the trackpad. It's hard to tell if it thinks it is "accidental input" or not enough pressure on the pad. It also likes to "run" along some sort of imaginary horizontal lines on the screen (elsewhere on the internet I've seen it described as a grid). I've read about people editing their xorg.conf and changing the input pressure and such, but with ubuntu 10.10 they've split the xorg.conf file up into several files. Any guidance?
No guarantees that this advice applies to a Mac trackpad, but after some fiddling, I found that the following Touchpad settings worked best for me on an Acer AA1 netbook:

**General**
Check: Disable touchpad while typing
Uncheck: Enable mouse clicks with touchpad

**Scrolling**
Disabled

> Screen dimming/sleep problem:
My screen likes to randomly dim itself when I'm using it, or not follow my power consumption configuration. It's speradic as to what's going on here, so I don't know that I can correctly describe it yet. Also, my mouse doesn't work when the screen dims and I have to use the brightness+ key to rewake the desktop. No other button seems to work, or the mouse. I have a similar problem when opening/closing the laptop, too. Sometimes it awakes, but several times I've had to restart because I can't do anything.[/QUOTE]
I may have had a similar problem with the screen brightness varying unpredictably. Try going to Control Center > Power Management, and uncheck the "Dim display when idle" box. For the "On Battery Power" tab, there is an additional checkbox: "Reduce backlight brightness". Uncheck that one also. 

Since there are different options for the on AC and on battery tabs, I choose "Blank screen" when on AC, and "Suspend" when on battery. With Blank screen, it starts up faster when you open the lid, because it's not completely asleep, while Suspend puts the machine into a very low power state, but takes longer to wake up.

Also check your screen saver settings and, uncheck "Lock screen when screensaver is active. There are some other settings that affect authentication, but they are a little harder to get to.

Good luck.

---

### Post by martank on 2010-12-26
Thanks for the input, libssd. I think that may have fixed my random-brightness issues, and it appears that my power management has reached some sort of happy medium as well.

I already had those settings for my mouse. Maybe I can describe this better.The trackpad randomly drops sensing my finger's input. I'll make a gesture with my finger (and I don't mean multitouch; my two finger scrolling works fine) and the mouse won't move. This can also happen mid movement, where I'll be trying to move across the screen and the pointer will just cease moving, and it'll take me a couple drags before it gets going again. 

Any other input?

Thanks!

---

### Post by libssd on 2010-12-26
Batting .500 is pretty good in baseball. ;) Since I have no direct experience with Ubuntu on a Mac, you're going to have to wait for a reply from someone with more experience. You may have better luck asking this question in the _[Apple Users]("http://ubuntuforums.org/forumdisplay.php?f=328")_ forum.

---

### Post by martank on 2010-12-26
Trying there now; thanks again.

---

