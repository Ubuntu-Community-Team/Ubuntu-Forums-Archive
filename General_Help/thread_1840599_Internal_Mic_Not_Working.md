---
title: "Internal Mic Not Working"
date: 2011-09-07
forum: General Help
---

### Post by carmenat250 on 2011-09-07
I am running Ubuntu 10.04 and when I first installed it, the internal mic was working perfectly.  I didn't have to manually install any drivers, etc.

I went to use it today within Gmail and noticed that no one can hear me on the internal mic.

I have made no changes to the system that I can think of.  As I am a Linux newbie, I'm really not sure how I'd go about troubleshooting this problem.

Thank you

---

### Post by mmsmc on 2011-09-07
did you un-mute it in system sounds?

---

### Post by carmenat250 on 2011-09-07
> **mmsmc said:**
> did you un-mute it in system sounds?

If I go into sound preferences and I look at the output volume, it is set to 100% and is not muted.

---

### Post by mmsmc on 2011-09-08
ok, now just to be sure, that out put volume is 100% for everything(mic, sound, etc)
and, are you only using ubuntu? or are you dual booting

---

### Post by carmenat250 on 2011-09-08
> **mmsmc said:**
> ok, now just to be sure, that out put volume is 100% for everything(mic, sound, etc)
and, are you only using ubuntu? or are you dual booting

No luck, the mic is still not working.  I am only using Ubuntu, no dual booting.

Not sure if this helps, but I've uploaded 5 screen shots of my settings.

[http://imageshack.us/photo/my-images/714/60310418.png/](http://imageshack.us/photo/my-images/714/60310418.png/)
[http://imageshack.us/photo/my-images/545/72203065.png/](http://imageshack.us/photo/my-images/545/72203065.png/)
[http://imageshack.us/photo/my-images/196/26295737.png/](http://imageshack.us/photo/my-images/196/26295737.png/)
[http://imageshack.us/photo/my-images/20/53514658.png/](http://imageshack.us/photo/my-images/20/53514658.png/)
[http://imageshack.us/photo/my-images/196/48682447.png/](http://imageshack.us/photo/my-images/196/48682447.png/)

---

### Post by Lighthorse01 on 2011-09-08
Ummm I hope someone comes up with something.I have a similar
problem. Using PulseAudio server on ubuntu 11.04 64-bit , not sure 
if there is a better Audio server,
Sound Recorder will record sound and vocal though not a good quality
but Skypy does not see or sound does not go through, so no vocal in
calls

---

### Post by mmsmc on 2011-09-08
its most likly a driver, if you have the drivers ad utilities cd install the driver for the mic, if ot go to your computer maufacturers website and dowload the driver form there

---

### Post by Lighthorse01 on 2011-09-08
And if there are no drivers for Linux ??

---

### Post by mmsmc on 2011-09-08
ok, lets try this, in the hardware tab in the volume control, choose the profile, are their any options for enabling/choosing the mic? try this also with the input tab > connector

---

### Post by Lighthorse01 on 2011-09-09
> **carmenat250 said:**
> I am running Ubuntu 10.04 and when I first installed it, the internal mic was working perfectly. I didn't have to manually install any drivers, etc.
 
I went to use it today within Gmail and noticed that no one can hear me on the internal mic.
 
I have made no changes to the system that I can think of. As I am a Linux newbie, I'm really not sure how I'd go about troubleshooting this problem.
 
Thank you
 
install pulseAudio Volume Control
then be sure your mic is running as mono if not change either the left or right
channel to 10 and the other to 90

---

