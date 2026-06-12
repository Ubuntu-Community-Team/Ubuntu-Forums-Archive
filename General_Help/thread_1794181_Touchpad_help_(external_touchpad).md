---
title: "Touchpad help (external touchpad)"
date: 2011-06-30
forum: General Help
---

### Post by techno-mole on 2011-06-30
Hello.

I have just got hold of a touchpad, it's and old one the drivers are for windows 95/98 so I thought I'd have a go and see if I can get it working.

It connects to a serial port (9 pin) I have plugged it in but nothing is happening, I know it works because I tried it on Windows 7 to see what would happen and it installed a driver (generic input device driver) and the touchpad worked fine.

But in Ubuntu nothing, and to be honest I'm not sure how to proceed, I tried using xinput list but didn't see anything that I thought might be the touchpad.

Here's the output for " xinput list "

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 062a:0000                           	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Trackball                  	id=11	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=12	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=13	[slave  pointer  (2)]
&#9116;   &#8627; USB-compliant keyboard                  	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AVerMedia A815                          	id=9	[slave  keyboard (3)]
    &#8627; IR-receiver inside an USB DVB receiver  	id=10	[slave  keyboard (3)]
    &#8627; USB-compliant keyboard                  	id=14	[slave  keyboard (3)]

```

Would it be worth getting an adapter ? like a serial to usb or one of those serial to ps/2 adapters and see if it works then ?

I can't really give much info on the touchpad other than it appears to be made by " Fine ART Tech " but I haven't been able to find out much about them, it's called an " ICON TouchPad " it has 3 buttons, left click, right click and what I think might be a scroll button or back / forwards button. It should be used with a stylus but it seems to work fine if you use fingers (like you would with a laptop)

I know this isn't life threatening but I would like to see if it's possible to get it to work on Ubuntu.

I'm running Natty 64bit, with unity (I'm one of the few that seems to like it)

Anyway if anyone has any pointers I'd appreciate the help.

Cheers.

---

### Post by techno-mole on 2011-07-01
*Bump*

No one fancy a bite at this ? 

Well just to update I got hold of an adapter to go from serial to ps/2 figuring it might work as a mouse on ubuntu and nothing, so I'm going to do a little more research.

Cheers.

---

### Post by Favux on 2011-07-02
Hi techno-mole,

The usb UC-LOGIC tablets use the wizardpen X driver from DoctorMO's PPA:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

I sort of doubt the current wizardpen X driver has serial tablet support but I don't know for sure.  I don't recall ever seeing anything about a UC-LOGIC serial tablet but I'm pretty sure you would need a X driver specifically written for a serial device.

We have been able to get an old SummaSketch serial tablet "working" by using inputattach and the evdev X driver:  [http://ubuntuforums.org/showthread.php?t=1784259](http://ubuntuforums.org/showthread.php?t=1784259)  Inputattach translates the incoming serial data stream into usb data and places it on the input subsystem, i.e. /dev/input/? like an usb device.  With luck one of the inputattach protocols would work for your UC-LOGIC tablet well enough that the wizardpen driver would then actually work with it.  You may have to create a match for your tablet in the 70-wizardpen.conf to place it on the wizardpen driver if you get that far.  You'd use *xinput list* to find the correct keyword(s).

---

### Post by techno-mole on 2011-07-02
I think I should have explained things a little better, perhaps putting the output from xinput has mixed things up.

This isn't actually a tablet, it's an external touchpad, like you'd get built into a laptop only this thing connects via the serial port.

It's like this, [http://tinyurl.com/6adblso]("http://tinyurl.com/6adblso") but has an extra button and connects using the serial port

It does work on windows 7, although I've yet to find a way to configure the thing, I'm assuming that there isn't any kind of driver in the kernal that will run it, I do have the original driver disc, which is for windows 95/98, which is pretty archaic now.

I have tried a serial to ps/2 adapter but nothing happened, I'm now wondering whether a serial to usb adapter might work, but I need to look into it as these adapters need a driver to run, so I might be faced with having to find a driver for the adapter and possibly the touchpad as well, I'm not sure how well supported these kinds of adapters are on linux / ubuntu.

Cheers for the reply, I will look into the things you mentioned though I might find something that helps, my tablet (the uc-logic) works flawlessly in natty, it works without the wizardpen driver, but does work better with it installed :-)

Cheers again.

---

### Post by Favux on 2011-07-02
> It should be used with a stylus but it seems to work fine if you use fingers (like you would with a laptop)
Well either way, tablet or touchpad, since it is a serial device inputattach is proably the way to go.  Unless maybe you have a converter lying around.

And you're right, depending on the serial-to-usb converter manufacturer, installation can go from plugging it in to writing code for the converter kernel driver.  Research definitely needed.

---

### Post by techno-mole on 2011-07-03
Right I've been playing around with inputattach, not sure I'm doing anything right but I figured the best thing to do was find out what name the device has so I basically started running various things.

as an example running ```
sudo inputattach --always -vs /dev/ttyS0
``` and the running "xinput list" gives me the following.

```
DEC VSXXX-AA/-GA mouse or VSXXX-AB digitizer	id=16	[slave  pointer  (2)]

```

I've run all the things from the thread you linked to and basically got the same results from xinput list but the touchpad still doesn't respond, however I noticed if I run this (again from the thread you linked to)
```
sudo inputattach --always -t213 /dev/ttyS0
```

I get a response from the touchpad, it's very erratic and the pointer only goes to the top right of the screen (had this with my tablet from time to time) so I'm wondering if I should attempt to get it set up as a tablet and see how far I get, seeing as it doesn't respond as anything else, I've been through everything from here [http://manpages.ubuntu.com/manpages/natty/man1/inputattach.1.html]("http://manpages.ubuntu.com/manpages/natty/man1/inputattach.1.html") and the only thing I get is from running ```
sudo inputattach --always -t213 /dev/ttyS0
``` I'm still unable to find out who made it, the only company that has a similar name seems to make security equipment ? so I doubt I'll get much help from them.

I'm still looking into the serial to usb adapters to see if I can find one that will work with ubuntu.

cheers.

---

