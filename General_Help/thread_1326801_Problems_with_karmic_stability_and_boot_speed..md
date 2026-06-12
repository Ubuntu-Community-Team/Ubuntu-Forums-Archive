---
title: "Problems with karmic stability and boot speed."
date: 2009-11-14
forum: General Help
---

### Post by Romanrp on 2009-11-14
I have returned from opensuse to ubuntu.
now,
I had to reboot a few times because my system froze-nothing much,just a game got stuck.
Boot time is nothing special-not as fast as everyone says.
I just want to make sure that is it my machine or is it karmic?
I have 4g ram and core2 duo 2.10 ghz processor.
I  run 64bit ubuntu.
Is there anything I can do to make the boot speed faster so I can really feel it?
And what might be causing the instability?

---

### Post by user333 on 2009-11-14
I upgraded to Karmic, and my boot time tripled :( I don't know, but I think it might be the new xsplash, not your machine. I just put up with it, and hoped that 10.04 will be better. I think your computer is fine, but I know nothing about 64 bit. I have 32.

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
I noticed a difference in boot time as well. Sounds like it's an issue with 64 and 32 bit. I don't see any reason to complain but mine is only about 10 seconds longer than my 9.04 32 bit install (soon to be removed). The only way I know of to make boot faster is to disable some of your features. I'm sure a Google search would bring up some ways to do so. How slow is it?

About freezing... what game was it? I'm running a bunch of games in and out of wine and I've had no problems insofar except with Star Trek Armada 2 in wine losing the buttons sometimes.

---

### Post by Romanrp on 2009-11-15
The game is wolfenstein.
It just crashes.
It crashes so much that I can't even acces the full terminal mode with ctrl+alt+f1.

---

### Post by jeb800e on 2009-11-15
Restart your system and load into the GRUB. Select an older kernel. This may fix your problem. 

You can also pick a "recovery mode" of these kernels, as well, if you need to fix something or recover something.

---

### Post by wojox on 2009-11-15
Haven't tried it personally ( karmic mini boots in ten seconds ) [http://www.ubuntugeek.com/ubuntu-tip-increase-your-boot-times-with-ubuntu-boot-in-karmic.html](http://www.ubuntugeek.com/ubuntu-tip-increase-your-boot-times-with-ubuntu-boot-in-karmic.html)

---

### Post by Romanrp on 2009-11-15
Yo frankie also crashes. So much for stable os.
How do I load into grub? Do I press esc?
And will choosing an older kernel break my system?
Does the ubuntu netbook remix function as well as the big distro?
will i see improved performance if I swap to the netnook remix,maybe downgrade to jaunty?
Is there any other good .deb based linux with gnome preinstalled?
 by the way sorry for all these questions.

I am thinking og getting rid of some startup apps.
this is the list: (which ones do I need to keep in order of have a working system and which ones can go?)
AT SPI registry wrapper
Disk notification
gnome keyrig daemon
gnome settings daemon
gnome setings daemon helper
indicator applet
policykit authentication agent
seahorse daemon
user folders update

These are the ones i am not sure about,the rest were taken care of.

---

