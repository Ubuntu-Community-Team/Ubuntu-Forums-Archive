---
title: "Only 1 application can use sound device"
date: 2010-01-25
forum: General Help
---

### Post by woop11 on 2010-01-25
Hi

Im using Kubuntu 9.10 and each of my sound devices can only be used by 1 application (e.g. if amarok is using my speakers smplayer cant).

Any idea how i could work around this?

---

### Post by MatesCZ on 2010-01-25
I've had the same problem earlier, try this, it helped me:

1. Install pulseaudio
> sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter
2. Run PulseAudio preferences
> paprefs
3. In Simultaneous Output tab check the &#8216;Add Virtual output for simultaneous output on all local sound cards&#8216; checkbox.

---

### Post by woop11 on 2010-01-26
Thanks a lot, its working now :)

---

