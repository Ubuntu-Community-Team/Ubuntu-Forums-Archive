---
title: "Cannot get my external speakers to work"
date: 2010-02-25
forum: General Help
---

### Post by petedes5 on 2010-02-25
I have 9.04 and have googled and read every imaginable thread and have tried many different things to Ubuntu to recognize my external speakers to no avail.

can someone please help me out? my laptop speakers work perfectly, it's when i plug in my external speakers that there is no sound.

---

### Post by Johnny B on 2010-02-25
are you pluging into the headphone jack?
if so, do the internal speakers still work?

do your external speakers have a indicator light that works?

---

### Post by petedes5 on 2010-02-25
Yes, I am plugging it into the headphone jack. When I plug the cord into the jack my built in speakers shut off. The only light on my speakers is the power light.

---

### Post by Johnny B on 2010-02-25
the reason i asked about the indicator light is that the internal speakers are hardwired to the jack, so you don't need ubuntu to recognize them, its a hardware problem, make sure your speakers work with another device.

---

### Post by petedes5 on 2010-02-25
My speakers work perfectly fine with my macbook, it's not the speakers

---

### Post by Johnny B on 2010-02-25
perhaps its in the laptop or jack, try pluging headphones or something else into it

---

### Post by petedes5 on 2010-02-25
I know for sure it's not the laptop or any hardware. It's Ubuntu, I am a beginner to ubuntu so i might not have the right details checked or unchecked or the right software installed, i think that is where the problem lies.

---

### Post by Johnny B on 2010-02-25
I am still assuming the laptop speakers are hardwired to the headphone jack, especially if they shut off when the jack is used. 
can you boot the live CD or another OS to test the speakers?

---

### Post by chewearn on 2010-02-26
> **petedes5 said:**
> I know for sure it's not the laptop or any hardware. It's Ubuntu, I am a beginner to ubuntu so i might not have the right details checked or unchecked or the right software installed, i think that is where the problem lies.

Double-click on the speaker icon (top right of the desktop).  Check any (related) output is not muted and volume is set at appropriate level.

---

### Post by petedes5 on 2010-02-26
everything is checked and at appropriate volume. I've also did the whole terminal: "alsamixer" and played around in there to no avail.

I think it maybe my sound card and ubuntu mis-communicating. 

--- I just had Windows 7 running on this computer and my external speakers worked fine.

---

### Post by petedes5 on 2010-02-26
this is unbelievable now....
\


I managed to delete my entire alsamixer by following this website

[http://www.webupd8.org/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html](http://www.webupd8.org/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html)

---

### Post by petedes5 on 2010-02-26
reinstalled ubuntu and still the same problem, the external speakers are not working!

---

### Post by petedes5 on 2010-03-01
.

---

### Post by chewearn on 2010-03-01
Can you post the sound hardware info.

Here is how to troubleshoot sound problem:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by petedes5 on 2010-03-01
In preferences/sound: 

Sound Playback: autodetect

Sound Capture: ALSA

Device: HDA Intel (Alsa MIxer)

Sound Card: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller

Everything is unmuted and I have played with muting and unmuting to no avail.

jaunty, i have 9.04

---

### Post by petedes5 on 2010-03-02
up

---

