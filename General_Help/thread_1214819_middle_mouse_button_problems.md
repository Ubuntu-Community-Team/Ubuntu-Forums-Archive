---
title: "middle mouse button problems"
date: 2009-07-16
forum: General Help
---

### Post by Netmonger on 2009-07-16
Hey.. Im wondering if anyone else is seeing something like this with 9.04.

My middle mouse button doesnt work, and its driving me totally nuts on my office desktop. Its not application specific but affects *everything*: paste in terminal, resizing windows with 'alt' key, firefox open new tab, etc..  

Ive tried 2 different brand mice, Ive messed around with xorg.conf, and I still cant get this to work right.

The scrollwheel works fine - its just pressing the middle mouse button thats a problem.

I ran 'xev' and watched the events being generated and when I hold the middle mouse button down, you can see constant ButtonPress and ButtonRelease events occuring non-stop - as if you were clicking it really quick. This doesnt happen with the left/right mouse buttons. The same thing happens with two different brand wireless mice, one which is brand new as I bought it to diagnose this problem.

The behavior is intermittent. It seems like if I mess with the scroll wheel while pressing the middle mouse button, sometime I can get it to work right - like a quarter of the time.

Has anyone else seen this?  I am using a separate PS2-USB converter for my keyboard, but this was all working fine with the identical mice in earlier Ubuntu releases.

Its really messing me up as I am so used to using the middle mouse button for paste.

Its worth mentioning that this only happens with my office desktop - my home workstation works fine.

---

### Post by jonobr on 2009-07-16
It may help if you run xev
OPen terminal type xev and a debug window and a box will open.

Put your mouse over the box, scroll up and scroll down, you will see debug.

The try pressing your button and see if you get anything.

---

### Post by Netmonger on 2009-07-16
Tried this. The weird thing is that when I hold down the middle mouse button, I see a constant stream of ButtonPress and ButtonRelease events - as if I was clicking the button really fast.

This does not happen with the left or right mouse buttons.

I was poking around in Xorg.0.log and saw a bunch of messages about Macintosh mouse emulation, and 'emulateWheelButton', etc..  - not sure if this is related. 

This is driving me completely bonkers as I need to be able to paste with middle mouse button.

---

### Post by jonobr on 2009-07-16
AFAIK and open to correction on this, thats odd,

You should be seeing one for depress and one for release.
If you hold down, you should see one until the release.


On the mention of macintosh, no I dont think its relevant.

Im using a logitec usb optical and here is the result
cat Xorg.0 | grep mouse


> II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse


If you were sing the same mouse, maybe I could get you a config file or something?

---

### Post by Netmonger on 2009-07-16
Ive messed around with xorg.conf, but in 9.04 its mentioined that the configuration is automatic, and this config block is ignored?

I actually have a trackpoint keyboard with built in 'mouse' connected to the same machine, but I just tried removing it completely, with same results. Also the whole setup worked fine in previous versions of Ubuntu.

To make matters worse, I actually had better, although still intermittent, middle mouse button functionality before I started messing around with this. And even though Ive removed the configuration from xorg.conf, it pretty much flat out refuses to work now.

Im wondering if there is some kind of emulation thing going on which causes the flurry of ButtonPress/ButtonRelease events.

Arrrrgggh!!!!   :)

---

### Post by jonobr on 2009-07-16
Man your in for a disappointment with the answer IM about to give.

It sounds like it, but what, I dont know... :-(

On it being ignored, that was new on me?

Maybe posting your xorg.conf as it is may help

---

### Post by jonobr on 2009-07-16
I saw this post also [Here]("http://ubuntuforums.org/showthread.php?p=7626526#post7626526")

I wonder is this a frequent problem for middle wheel users on 9.04.

Mine appears ok..

---

### Post by Netmonger on 2009-07-16
Yeah I was surprised too!  On a brand new 9.04 install, /etc/X11/xorg.conf is almost blank, and the following text is at the top of the file:

[COLOR="SlateGray"]# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.[/COLOR]

---

### Post by Netmonger on 2009-07-21
Just an FYI.. These problems only happen when using wireless mouse.. With a wired mouse, there is no flurry of 'buttonPress/buttonRelase' events, and the middle mouse button works as expected..

---

