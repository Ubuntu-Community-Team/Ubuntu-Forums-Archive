---
title: "eee901 crashes when external monitor plugged in"
date: 2010-01-04
forum: General Help
---

### Post by nigelmouse on 2010-01-04
Hi, 

I've done a search and couldn't find mention of this particular problem, I hope I haven't missed something obvious though.

I have an Asus eee901 netbook and it's got an Intel 945 graphics card. If I boot it up, log in, attach an external monitor and then open the Display Settings dialog the screen goes black and the laptop appears to crash. Leaving it for a minute or two does nothing.

However, if I boot up with the external monitor attached then I can open the Display Settings dialog and configure both screens.

This is quite annoying as I've got to reboot if I want to connect an external monitor.

Additionally, if booted with the monitor attached and I choose a configuration where the width of the combined screens is greater than 2048, the screens go black and the same lock up appears to occur. Could it be that the Display Settings dialog isn't checking for the maximum display width the driver supports and is then crashing in both scenarios?

If anyone has any ideas of how to fix this, or how to log it as a bug please let me know.

This is all on 9.10 with compiz enabled.

Thanks

Nigel

---

### Post by t0p on 2010-01-04
I can't offer any specific help.  Though I can suggest [forum.eeeuser.com]("http://forum.eeeuser.com/") for EeePC support.  Ubuntu bug reports are made at [launchpad.net]("http://launchpad.net"). 

I'd like to ask a possibly stupid question: why can't you attach the external monitor before you boot your 901?  Whenever I use my 701 with an external monitor, I boot with it attached then use grandr to configure the display.

---

### Post by nigelmouse on 2010-01-04
> **t0p said:**
> I can't offer any specific help.  Though I can suggest [forum.eeeuser.com]("http://forum.eeeuser.com/") for EeePC support.  Ubuntu bug reports are made at [launchpad.net]("http://launchpad.net"). 

I'd like to ask a possibly stupid question: why can't you attach the external monitor before you boot your 901?  Whenever I use my 701 with an external monitor, I boot with it attached then use grandr to configure the display.

I can attach a monitor before I boot, but there's many situations where I've already booted my laptop and then I go to connect it to a TV or projector. In these situations it means I've got to shut down, attach, then restart.

It's also a pain because the eee 901 lcd panel is 1024x600, and when booting up with a screen attached it then switches to 800x600 (I'm presuming this is a mode that both the internal and the attached external screen are capable of). The switch to 800x600 messes up the layout of the icons on my top panel as I've got more than 600 pixels worth of icons there.

---

### Post by nigelmouse on 2010-01-04
I've just searched launchpad and found the following:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328)

and 

[https://bugs.freedesktop.org/show_bug.cgi?id=23718](https://bugs.freedesktop.org/show_bug.cgi?id=23718)

which appear to say this bug is fixed. 

Given it was set to fixed on 18-12-2009 I'm guessing that this was fixed upstream and may take a while to get into the karmic updates.

I may give xorg-edgers a try to see if the fix has been put into their build yet.

---

