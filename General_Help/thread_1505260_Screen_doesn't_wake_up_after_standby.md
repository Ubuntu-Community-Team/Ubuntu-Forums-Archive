---
title: "Screen doesn't wake up after standby"
date: 2010-06-08
forum: General Help
---

### Post by Helios747 on 2010-06-08
Hello,

When I put my laptop to sleep (clamshell close) it goes to sleep and is a happy laptop.

When I open the laptop, I can hear the thing going and waking up. However the screen stays off. Brightness keys do nothing. (however they did nothing in the first place as I'm using the NVIDIA driver). I have to do a hard reset to fix things.

The strange thing about this is Sleeping / Waking up has never been an issue til about today.

Any ideas?

Ubuntu version: 10.04 (has all updates)

Laptop: MacBook 5th gen (5.1, Aluminum)

Graphics chip: NVIDIA GeForce 9400m

Graphics driver: 173 (installed through restricted drivers)

---

### Post by quixote on 2010-06-10
I had a similar issue with different hardware, and the problem turned out to be the graphics driver not interacting right with the suspend routine.  There's a new open source driver for Nvidia graphics, called [nouveau]("http://nouveau.freedesktop.org/wiki/") which you can install using synaptic. ("xserver-xorg-video-nouveau", but you can also just search for nouveau in synaptic.)  For me (I have a Dell) the nouveau driver was way *better* than Nvidia's own drivers!  I don't know if it'll be the same with your hardware, but it's worth a try.

---

### Post by Helios747 on 2010-06-10
Hmm. That might be worth looking into. Maybe it will fix my brightness keys not working too!

The only concern I have is performance. I do play a couple games (Nexuiz, CoD4 (WINE))


But, I will look into this and report back my results!

---

### Post by Helios747 on 2010-06-10
Oh... That open source driver doesn't support OpenGL yet.

That's a shame, it looked really good.

---

### Post by quixote on 2010-06-10
Well, another thing to try, if all this worked under, say, karmic, is to downgrade to the driver version you were using then.  As I recall, I had to know exactly which version number I needed, install with apt-get specifying the whole name and version, and then lock it in synaptic so it wouldn't get updated.

But that all depends on there having been a version that worked.

---

### Post by Helios747 on 2010-06-10
Okay, I think I found the problem. I noticed today that none of my games would launch, complained about not having the correct drivers loaded. So I had a hunch that the NVIDIA drivers were borked. I uninstalled the drivers, rebooted, reinstalled, rebooted again, and now my games work, and standby is happy again.

I'm going to mark this as solved now.

ALTHOUGH! I am going to look into getting a dual xorg config setup so that the opensource driver is used for all of my desktop work (brightness keys work!). The NVIDIA driver  would kick in with games as I launch games in their own xserver. I could probably fiddle with the command to make it use an alternate xorg config file which loads the NVIDIA driver.

---

