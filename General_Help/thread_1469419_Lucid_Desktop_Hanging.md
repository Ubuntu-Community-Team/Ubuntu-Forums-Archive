---
title: "Lucid Desktop Hanging"
date: 2010-05-02
forum: General Help
---

### Post by AP0ll0UK on 2010-05-02
Apologies for posting here, I don't seem to have the option to post in the Lucid forum anymore.

I installed some updates as suggested by the os yesterday but ever since then, the box has become very unstable. Moving the mouse cursor around the desktop and navigating around works ok for about 5 minutes after the box has booted up, but after that it runs very very slowly and sometimes appears to hang. 

VNC won't connect to the box after 5 minutes or so although I can still connect to the box through a browser and it appears ok. I can also access my fileshares on the box from my laptop ok but video playback is hit and miss, it's ok for a couple of minutes and then hangs, then carries on.

Prior to these updates being installed on the system it's been working perfectly for the past couple of months and I've been very pleased with.

Does anyone have any ideas please?

---

### Post by dino99 on 2010-05-02
see into htop what is eating your ram

sudo dpkg --configure -a
sudo apt-get install -f

install gconf-cleaner and use it (yes to all)

---

### Post by AP0ll0UK on 2010-05-02
Ok, accoding to htop the box isn't under too much of a strain as per the attached image.

---

### Post by AP0ll0UK on 2010-05-02
Actually, the issue seems to occur after I run VNC, the box doesn't normally have a mouse and keyboard connected to it so the only way I can get to it normally is through VNC.

I reinstalled VNC, rebooted and the box came back up and was fine, I ran the System Monitor and all was looking good. Then I tried to connect to it from VNC, ok for the first few minutes and now the desktop appears to have hung. The System Monitor has stopped, I can't click on anything, the mouse cursor moves but anything I click on simply doesn't respond.

From VNC it looks like the attached screenshot and has stopped responding altogether. The only way to get it back is to reboot. And running htop whilst the box is in the this semi hung state, everything looks normal and I can still access my fileshares and apache - I'm very confused.

---

### Post by AP0ll0UK on 2010-05-02
Correction, it is what I first thought, it locks up at random within a few minutes of booting, not just when I Vnc to it.

Oddly enough for the first time I've rebooted it and it's showing an i/o on one of my discs.

The frustrating thing is that I can't keep the box up for long enough to get it, unmount it and scan it before the box locks up.

Help!

---

### Post by dino99 on 2010-05-02
need to dig out the logs

---

### Post by AP0ll0UK on 2010-05-02
I've had a quick look through the logs but there are tons to go through. 

Can you point me in the direction of the important ones please?

Or alternatively, as it is the desktop that is hanging after a few minutes and not the machine, can I access the important logs easily through SSH?

I've managed to get some info about the disc thats failing, it's reporting 'Reallocated Sector Count'. The thing is, when I'm browsing around that drive it's fine, the desktop usually hangs when I'm doing another task, often on another drive.

I've unmounted the disk thats having issues but running scans against it doesn't come back with much to be honest. Does Ubuntu have anything built into it to identify bad sectors, isolate them and then not use them?

---

### Post by AP0ll0UK on 2010-05-08
Bump

---

