---
title: "Still no sound, tried everything"
date: 2009-11-12
forum: General Help
---

### Post by mdsftw on 2009-11-12
I've visited many forums and tried numerous things to get my sound working, but still no success. I'm using ubuntu 9.04 and when my laptop boots it makes a sound like it is hanging. So there's definetly sound coming out of my speakers (built in) but not the right sound.
I'm also a noob, so please explain it simple.

Thanks in advance.

---

### Post by Tiganjero on 2009-11-12
Use this thread, very helpful and simple.
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
Hope I helped :P

George

---

### Post by prakreet on 2009-11-12
go to system> administration > system testing. there u can test whether ur sound card is correctly detected...

at first there are many options to speak through a microphone and hear ur speech played back to u.. u can test ur sound here... or if u skip those and click on next many times u will reach a page where a recorded sound will be played back..

---

### Post by mdsftw on 2009-11-12
Thanks for the quick reply, but my sound is still not fixed. I followed every step but I still get no sound. I do get a hanging sound when I set the volume to maximum.
But the tutorial said that it only works if you hear a login sound when you log in. But I don't have that sound.

---

### Post by Tiganjero on 2009-11-12
Do you have a speaker icon in your taskbar? If not open up terminal and enter this
```
alsamixer -Dhw
```
Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty).
Tell me if there are any changes after that...
Regards

George

---

