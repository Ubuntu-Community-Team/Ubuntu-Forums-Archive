---
title: "Sound Card stopped working!!!"
date: 2006-04-23
forum: General Help
---

### Post by lokeey on 2006-04-23
need some help getting my sound card to work on my laptop. this happened to me before and i ended up doing fresh install, but i'm not looking to do that again. it was working fine since i installed Ubuntu. i shutdown my laptop earlier today to head into work. i get to work and booted up my laptop and i got an ALSA error. i checked out my messages log and saw the following error...

**[COLOR="Red"]VIA 82xx Audio: probe of 0000:00:11.5 failed with error -5[/COLOR]**

is anyone familiar with this error??? if so, what's the fix???

---

### Post by lokeey on 2006-06-12
I figured out what happened here. Just in case some of you experience this on your laptops, here's what happened.

I have a wireless mouse. Before shutting down or logging off or letting the process complete, I pulled out the USB wireless mouse from the usb port. This apparently affected the way it started up the next time around, and it prevented the sound from working. I don't know why it would affect this, but it did as I was able to replicate the problem.

---

### Post by TTL on 2007-10-21
I had the same error. On my system, it  helped to unload the modules cx8800, cx88_alsa and cx88xx (they had provided a sound device too). Then loading snd-via82xx once again and it worked without the error. Now I will blacklist the three modules above.

---

