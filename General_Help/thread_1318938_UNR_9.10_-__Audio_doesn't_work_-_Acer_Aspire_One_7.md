---
title: "UNR 9.10 -  Audio doesn't work - Acer Aspire One 751h"
date: 2009-11-08
forum: General Help
---

### Post by slooksterpsv on 2009-11-08
Tonight I just upgraded to UNR 9.10 - I was previously use UNR 9.04 - I have install the GMA500 drivers (Poublsa something like that - kernel drivers what not). Anyways I cannot get my sound to work. I ran a command as was specified in another thread:
shawn@shawn-acer-ub:~/Desktop/Songbird$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC272

I have kernel 2.6.31-14 Generic running. I don't hear audio out of the speakers on my system, I keep thinking I had to setup Pulse audio some how with my system, I tried a log where it had me modify asound.conf and restart alsa that failed.

Does anyone know how to fix this?

Side Note: Before I upgraded I updated all the packages on 9.04 then did the upgrade, I don't have any updates for 9.10.

---

### Post by slooksterpsv on 2009-11-08
Ok, it's fixed, I don't know what exactly made it work, but here's what I did:

I modified the alsabase file in modprobe.d and changed it to 
snd-hda-intel model=acer-aspire

Then I went and downloaded a couple of pulseaudio programs and codecs, next I opened PulseAudio Applet and clicked around, next I tested the sound after all that, and it's working. Haven't rebooted to see if it works when I reboot, if it doesn't and it's just the applet I'll have to modify it to where Pulse comes up instead of alsa.

---

