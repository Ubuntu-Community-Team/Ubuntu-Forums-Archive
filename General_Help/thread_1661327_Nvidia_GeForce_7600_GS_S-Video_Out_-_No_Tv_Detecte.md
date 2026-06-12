---
title: "Nvidia GeForce 7600 GS S-Video Out - No Tv Detected"
date: 2011-01-06
forum: General Help
---

### Post by mattgaunt on 2011-01-06
Hi everyone,

I've been Googling around to find a solution to this problem and can't see anything that really resembles this.

I've installed the restricted drivers for Nvidia and it recognises the VGA montior but doesn't register the attached TV through S-Video.

There are several posts on getting the TV to work when it appears in the nvidia-settings but it's not showing up.

I've tried installing different drivers through the Addition Drivers window and shutting down and starting up the machine each time, but nothing seems to work.

The main aim with this PC is to have it run just off of the TV. [Removing the VGA cable so the TV is the only thing plugged in didnt work, it just booted into the command line]

Anyone with any ideas please let me know. Any extra info I can give you from the command line Im happy to give.

Cheers,
Matt

---

### Post by lrgmmc on 2011-01-06
the info is a little old but may still be of assistance
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)
also 
[http://ubuntuforums.org/showthread.php?p=4929070](http://ubuntuforums.org/showthread.php?p=4929070)

---

### Post by mattgaunt on 2011-01-06
I did both of those, but the thread doesn't seem to help and while manually altering the xorg is fine, it just seems like the problem would lie else where since the start of the HOWTO is "This is deprecated for the GUI".

I'll give it a go tomorrow though and see if anything happens.

---

### Post by mattgaunt on 2011-01-08
Just gave editing the XOrg file a go and nothing changed, the tv remains and the nvidia-settings doesn't recognise it as being plugged in.

Does anyone have any other ideas??

---

### Post by mattgaunt on 2011-01-08
I just rebooted after changing between nvidia drivers and realised there was brief message about start Nvidia tv out, the only problem is it came and went far too quickly for me to notice. Does anyone know if these messages are logged and if so, where I can find them?

Cheers,
Matt

---

### Post by bratherlui on 2011-09-14
Hi there!

Don't know if you fixed it yet.

I had the same problem.
A year ago, after days of trying to get the accelerated drivers working with my TV plugged in my NVIDIA Gefore 7600 GS I just gave up. Since then I am using the NOT accelerated drivers. lshw say the drivers used are 'nouveau'. Nothing in my xorg.cfg, only TV plugged to card.

Bye there

---

