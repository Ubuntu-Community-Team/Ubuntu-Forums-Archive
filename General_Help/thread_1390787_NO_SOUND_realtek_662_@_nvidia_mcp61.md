---
title: "NO SOUND realtek 662 @ nvidia mcp61"
date: 2010-01-26
forum: General Help
---

### Post by Gabri3l on 2010-01-26
I'm sorry if this was alredy posted, but I recently installed ubuntu 9.10, today actually, and I can't seem to make the audio work. I read a lot of threads, but no luck with this... Please someone help, I'm just starting and don't know mucho of this things :frown:

---

### Post by t4thfavor on 2010-01-26
Its a common issue, I see on google lots of hits. 

Start here
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by amsterdamharu on 2010-01-26
Can you run the following command and post the output?

```

cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by Gabri3l on 2010-01-26
codec: Realtek ALC662 rev1

---

### Post by amsterdamharu on 2010-01-26
Have you tried the following:
[http://ubuntuforums.org/showthread.php?t=1388643#3](http://ubuntuforums.org/showthread.php?t=1388643#3)

And check out all the settings in volume control (the speaker icon in your panel somewhere)
In Volume control choose edit -> preferences and check every box that might have something todo with muted sound.

---

### Post by Gabri3l on 2010-01-26
> **amsterdamharu said:**
> Have you tried the following:
[http://ubuntuforums.org/showthread.php?t=1388643#3](http://ubuntuforums.org/showthread.php?t=1388643#3)

And check out all the settings in volume control (the speaker icon in your panel somewhere)
In Volume control choose edit -> preferences and check every box that might have something todo with muted sound.


I tried that, but the volume is not silenced, I followed every instruction in that thread but I still have no sound and it's weird becouse in another forum, a guy had the exact same sound card and problem, but he solved the problem (i must have done something wrong, but i checked it a hundred times) :confused:

This is what I did:
Codec: Realtek 662 rev1

Found the ALSA documentation:
3stack-dig    3-stack (2-channel) with SPDIF
  3stack-6ch     3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig     6-stack with SPDIF
  lenovo-101e     Lenovo laptop
  eeepc-p701    ASUS Eeepc P701
  eeepc-ep20    ASUS Eeepc EP20
  ecs        ECS/Foxconn mobo
  m51va        ASUS M51VA
  g71v        ASUS G71V
  h13        ASUS H13
  g50v        ASUS G50V
  asus-mode1    ASUS
  asus-mode2    ASUS
  asus-mode3    ASUS
  asus-mode4    ASUS
  asus-mode5    ASUS
  asus-mode6    ASUS
  auto        auto-config reading BIOS (default)

Typed this command: sudo nano /etc/modprobe.d/alsa-base.conf
And at the end of the file added "options snd-hda-intel model=3stack-6ch"

I guess I did everything ok, but ir still doesn't play anything...

---

### Post by amsterdamharu on 2010-01-26
Did you right click the speaker icon and choose preferences, there you should choose alsa if it's not already chosen. Double click the speaker and check volume, choose edit -> preferences here again and check any box that could mute the sound.

---

### Post by Gabri3l on 2010-01-27
> **amsterdamharu said:**
> Did you right click the speaker icon and choose preferences, there you should choose alsa if it's not already chosen. Double click the speaker and check volume, choose edit -> preferences here again and check any box that could mute the sound.

Noup, I've alredy done that and no luck :( I guess I'm gonna post this thread again so if anybody had this problem can help me, thanks a lot anyways :D

---

