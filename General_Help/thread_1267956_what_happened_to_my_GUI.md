---
title: "what happened to my GUI?"
date: 2009-09-16
forum: General Help
---

### Post by raymondvillain on 2009-09-16
Jaunty 64 bit on a desktop.  Yesterday everything was fine.  I shut down last night, and this morning when I booted, no graphics.  I get a text-only login screen.  Everything seems to be there (no files missing) but I can't figure out how to restore the familiar and necessary GUI.  I tried booting to recovery mode and fixing the graphics but that didn't do anything.

Any suggestions would be greatly appreciated.  Hope I don't have to re-install.

By the way, I have a motherboard with built in ATI graphics.  I know that is a black mark, but it was working pretty well.

---

### Post by danwood76 on 2009-09-16
Onboard ATI graphics should be fine, no black marks!

At the top of the text mode does it say ttyX? what is the number X?
If it isnt 7 try hitting Ctrl + Alt + F7, that is the graphical VT.

If that doesnt help when you are logged in in text mode try these two commands:
```

sudo /etc/init.d/gdm restart
startx

```
both of those should launch X

---

### Post by raymondvillain on 2009-09-16
Thanks, Danwood76.

That did something, but now I have what I guess is a graphics screen, but it is all garbled up.  Mostly broad stripes in black and white.

I booted to recovery mode and tried to autofix graphics.  Then I booted to a text prompt and typed in your instructions, but now the only way I can get out of the screen is to unplug the machine.

I can boot to recovery mode and try something else, if there's anything left to try.

---

### Post by danwood76 on 2009-09-16
Do you have a live CD?
If so stick it in and check that you get a graphical X with that and hope that it is no hardware issue.

If you can boot into a liveCD with a GUI then we can look to the X logs for errors.

in the terminal type this to search for errors:
```

cat /var/log/Xorg.0.log | grep '(EE)'

```
(I think I am aiming at the right file, Im at work in a windows only environment so I cant check)

That should hopefully spit out some errors and lead us in the right direction, post any output here if you can.

regards,
Danny

---

### Post by raymondvillain on 2009-09-16
When I type

cat /var/log/Xorg.0.log | grep '(EE)'

you mean I should be looking at the directory /var/log/ etc on the hard drive and not on the CD operating system?

I can boot to the live CD no problem and get a graphical environment.  Will work your suggestion momentarily, thanks for the help.

---

### Post by P4man on 2009-09-16
Did you by any chance install the restricted ATI driver just before that happened? I remember someone else with a similar problem who got that after installing the restricted ATI driver suggested by ubuntu. He fixed it by installing a newer driver from ATI's website. But im not sure how to install that driver without gui.

---

### Post by raymondvillain on 2009-09-16
Here are the (EE) lines from Xorg.0.log and Xorg.20.log:

> Xorg.0.log:
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
(EE) RADEON(0): Acceleration initialization failed

Xorg.20.log:
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) fglrx(0): XMM failed to open CMMQS connection.
(EE) fglrx(0): PPLIB: PPLIB is not initialized!.
(EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 0000000c, ulEventData = 00000001
(EE) fglrx(0): PPLIB: PPLIB is not initialized!.
(EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 00000002, ulEventData = 00000000
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.


Hope this helps.

---

### Post by raymondvillain on 2009-09-16
Thanks, P4man, but I did not install the restricted ATI driver.

---

### Post by P4man on 2009-09-16
Yeah, I noticed from your logs.

I think danwood know a lot more about this than me, so he might give you an *actual* solution, but as a temporarily workaround, try using the vesa driver

on your harddrive, edit
/pathtoyourdrive/etc/X11/xorg.conf

find the "device" section. It probably has "ati" or "radeon" in it now. Change it to vesa:

```
Section "Device"
   Identifier     "whateverwashere"
   Driver         "**vesa**"
EndSection
```

Will be sluggish, but will hopefully at least work.

---

### Post by raymondvillain on 2009-09-16
I remember now what is probably the cause of all this grief.  I was trying to get GoogleEarth running.  One fix, suggested in these forums, was to rename /lib/libcrypto.so.0.9.8 to something else and then make another change.  I tried that but it did not cure my GoogleEarth woes.  I didn't think it would wipe out my GUI because I continued to use the machine.

It wasn't until I booted up today that the problem became apparent.

Now I have restored libcrypto.so.0.9.8 but still do not have a GUI.

---

### Post by raymondvillain on 2009-09-16
I'm going to mark this one solved.

Went to /etc/X11 and found an earlier version of xorg.conf, restored it, and things are back to normal.

Wish I had thought of that sooner.

Thanks for all the help.

---

### Post by blur xc on 2009-09-16
> **raymondvillain said:**
> I remember now what is probably the cause of all this grief.  I was trying to get GoogleEarth running.  One fix, suggested in these forums, was to rename /lib/libcrypto.so.0.9.8 to something else and then make another change.  I tried that but it did not cure my GoogleEarth woes.  I didn't think it would wipe out my GUI because I continued to use the machine.

It wasn't until I booted up today that the problem became apparent.

Now I have restored libcrypto.so.0.9.8 but still do not have a GUI.


Might I ask what you problem was with getting Google Earth to run?  I ask because I chased my problem around for a while before finding my solution.

BM

---

### Post by raymondvillain on 2009-09-16
I installed GoogleEarth using synaptic.  It worked fine for a while.

Then one day it stopped working.  When I clicked on the icon, a window would appear with the word "GoogleEarth", then disappear after about 2 seconds.  Followed by nothing.

I tried un-installing, and re-installing from the repository (synaptic), and also from the GoogleEarth web site by downloading the binary.  Same performance, or lack of performance.

This may have come about because I was tweaking the graphics driver to perform special desktop effects.  But I'm not sure.  All I know is that GoogleEarth just quit.

---

