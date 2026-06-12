---
title: "edit xorg.conf via the live CD"
date: 2010-01-31
forum: General Help
---

### Post by bish84 on 2010-01-31
Hi guys,
In a bit of predicament.
I was (stupidly) messing around with xorg.conf. Then, next time i booted up i just got a blank screen. It's booting up fine, and i can hear the login jingle, but must've changed the display settings incorrectly.

Problem is, i can't get into recovery mode when grub is loading. It doesn't give me enough time to press esc, with the 'grub loading' message only visible for a nanosecond before booting up ubuntu.

So now i'm on the live cd. I've mounted the hard drive, and navigated to the xorg.conf file. I can open it, and see the offending text, but not edit it. Tried editing a copy of it and replacing the original, but permission denied.

Sorry for being a newb, i've only been with Ubuntu for a week. Could anyone tell me how to edit xorg.conf via the live cd, or give me other instructions on how to restore my system / display drivers.

I'm running Koala.

Thanks all

---

### Post by falconindy on 2010-01-31
9.10's Grub is different from 9.04. Holding down shift gets you into the new Grub's boot menu.

---

### Post by t4thfavor on 2010-01-31
Beat the esc key like 100 times before the grub prompt loads, and you will get in.--- OR they changed the method as stated above :( 

You could also let it boot all the way, and then press ctrl+alt+F1 then use the txt prompt to edit your file back to whatever works. That is probaly the easiest method.

With the liveCD, you can do it, you just have to mount the drive, and open the files as root save, and your done.

---

### Post by mechro on 2010-01-31
From the LiveCD do **gksudo nautilus**.

Rename your xorg.conf to copyxorg.conf or similar.

Reboot your installation and a new xorg.conf will be created.

---

### Post by bish84 on 2010-01-31
You guys are brilliant.
Fixed it via the Live CD.

And,falconindy is right, you have to press shift as Grub is loading to get into the recovery mode screen on karmic.

As a new Microsoft migrant, it's great to know that i can get extremely prompt, accurate advice on these forums. With my (numerous) MS problems, i'd post on forums, and generally have to wait for a week before some kid finally responded by telling me that i'm an idiot.

Opensource rules!

:D

---

