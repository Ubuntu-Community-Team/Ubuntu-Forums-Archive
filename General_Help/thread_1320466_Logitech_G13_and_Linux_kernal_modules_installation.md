---
title: "Logitech G13 and Linux kernal modules installation"
date: 2009-11-09
forum: General Help
---

### Post by Lord Funzo on 2009-11-09
Hey, i am trying to get my g13([http://www.logitech.com/index.cfm/keyboards/keyboard/devices/5123&cl=us,en](http://www.logitech.com/index.cfm/keyboards/keyboard/devices/5123&cl=us,en)) running on Ubuntu, i have attempted to use the following:

[http://www.nexoid.at/g13/](http://www.nexoid.at/g13/) a would be guide andddd...

[http://forums.logitech.com/t5/G-Series-Keyboards/Does-the-G13-work-with-Linux/m-p/286903](http://forums.logitech.com/t5/G-Series-Keyboards/Does-the-G13-work-with-Linux/m-p/286903)
post 5 is quite helpfull.

I install everything using sudo for insmod g13.ko and trying the make command for the folder with and without sudo.

Nothing seems to work, at best, i can make the screen on my g13 come on blank.  I am using 64bit version.

A persistent problem (may or may not be) is that the files under the kernal folder within the G13 folder seem to get deleted when the machine is restarted and i have no idea why, they a there after i 'make'.

Thanks very much for any help, if you have managed to get it working on your computer, i would be very interested to know how.  This is literally the last thing tieing me to vista and i really....really hate it.

---

### Post by Giblet5 on 2009-11-09
Isn't a G13 just a Lite version of the G15?

Try installing the G15 stuff and see if it works...

```
sudo apt-get install g15daemon g15macro g15stats
```

You should have the time displayed on the LCD.

Now run g15stats from a terminal window. You should have a CPU graph showing.

Now run g15macro. Hit the MR button, type some stuff, and hit a G key.

If it doesn't work, just remove the G15 stuff.

---

### Post by Lord Funzo on 2009-11-09
i will try it as soon as i get home, thanks for the promt reply :)

---

### Post by Lord Funzo on 2009-11-10
no luck im afraid, i downloaded all of the packages form the synaptic package manager to avoid getting dependency errors form a manual install, everything installs properly for the G15 put still i have no luck with the G13.  At best i can still only get the screen to stay blank.

Perhaps its something to do with my kernal files being deleted on restart? is there anything that can cause this?.  Note that im using sudo, not logging in as root.

Thanks,
     Nick.

---

### Post by Giblet5 on 2009-11-10
> **Lord Funzo said:**
> no luck im afraid, i downloaded all of the packages form the synaptic package manager to avoid getting dependency errors form a manual install, everything installs properly for the G15 put still i have no luck with the G13.  At best i can still only get the screen to stay blank.

Perhaps its something to do with my kernal files being deleted on restart? is there anything that can cause this?.  Note that im using sudo, not logging in as root.

Thanks,
     Nick.

No...

Installing just g15daemon will put a clock on the LCD (immediately after the install completes) if it's going to work at all.

I guess the G13 is waaay different. Sorry for the added trouble.

---

### Post by bobtown on 2010-02-18
I'm having the exact same problem and I'm about to give up.  Has anyone else out there made progress with the G13?

---

### Post by Miscni on 2010-04-29
I'm still trying, to get it to wok, but I am far from done...

You could check out this link here : [http://ubuntuforums.org/showthread.php?t=1253153&page=2](http://ubuntuforums.org/showthread.php?t=1253153&page=2)

---

### Post by Praxsis on 2010-08-17
The Nexoid driver has been updated to a userspace. Though I have to wait for the documentation because I ahve no idea how to install libusb1 or uinput.

---

### Post by Larissa on 2010-08-25
Maybe you want to join the G15Tools project:

[http://www.g15tools.com/node/219](http://www.g15tools.com/node/219)
> Support for the G13 device has recently been added to libg15 in SVN. We've already had one report of issues and an offer of a patch. If anyone else has a G13, can you please try the latest libg15 from SVN and report whether you have success or failure? This will be very helpful as we attempt to expand support for these devices.

---

