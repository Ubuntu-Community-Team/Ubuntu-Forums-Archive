---
title: "laptop suspends again after waking up"
date: 2009-11-18
forum: General Help
---

### Post by phissure on 2009-11-18
I have my laptop set to sleep on lid close.
When I close the lid, it goes to sleep just fine.
When I open the lid back up, it will wake up and flash the login screen.  But it will instantly go back to sleep, so I have to push the power button to wake it up again.

When I put it to sleep without closing the lid, it works fine.

Any ideas?

Software:
Ubuntu 9.10 x64
Hardware:
Dell Latitude D630

---

### Post by speakman on 2009-11-24
Same here using a Samsung NC10 netbook. 

Closing the lid suspends the computer, but opening the lid does not start it (and is not supposed to), I have to use the power button. 

But when waking it up after a suspend, it sometimes (but not always) goes back into sleep after a few seconds. Another push on the power button, and this time it always stays awake.

I've used everything between 8.10 and the current 9.10. This happened after upgrading to 9.10, and has never been an issue in earlier versions.

---

### Post by sabre2th on 2009-11-24
It's tired and doesn't want to get up yet  ;)

Really though... It sounds like Ubuntu might be getting confused by the sensor that detects you closing the lid.  A driver issue is my guess

---

### Post by jmjohn on 2009-12-05
I have this problem too.

---

### Post by riban on 2009-12-08
I also have a Samsung NC10 and this problem started when I updated to 9.10. It was not an issue with 9.04 (or if it was, I fixed it then forgot). I do remember fixing a similar problem in the past but can't remember what that was now. I think sabre2th may be on to something with the OS expecting the lid switch to be two state rather than the single close state. I was hoping to find a solution but I guess I will have to start looking at it myself...

---

### Post by speakman on 2009-12-08
No this has never been an issue before. It came with 9.10.

---

### Post by ikt on 2010-02-17
> **speakman said:**
> No this has never been an issue before. It came with 9.10.

Just bumping this issue up a bit in regards to this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/449685](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/449685)

Anyone got time to give 10.04 a spin?

---

### Post by hvbakel on 2010-02-17
This bug has now been fixed, but you need to enable the karmic-proposed repository to get it. See the following bug report for more info: [https://bugs.launchpad.net/bugs/425411](https://bugs.launchpad.net/bugs/425411)

---

