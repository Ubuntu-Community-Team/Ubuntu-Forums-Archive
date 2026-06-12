---
title: "Please help - ALSA crashes everything"
date: 2009-07-13
forum: General Help
---

### Post by 3pinner on 2009-07-13
Anything having to do with sound, primarily Totem and my Thunderbird (because I have it set t make a sound when receiving e-mail). Thunderbird won't even open.
 Anybody?

Thanks!

---

### Post by 3pinner on 2009-07-13
If I kill PulseAudio, everything works fine.
Is there a fix for this?

---

### Post by 3pinner on 2009-07-13
I found a troubleshooting guide for ALSA here;
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Followed the instructions on restoring sound stack to "the official Ubuntu Core" and still have the same problem.
The only way I can get it to work is to use System Monitor to kill PulseAudio.

There's gotta be a way to fix this to its original working state.

Forgot to note:
Ubuntu 8.10 Intrepid

Thanks

WEll after hours of searching, I finally figured out this is a known bug (at least to everybody  else but me!) and found a way to disable PulseAudio and everything works now. Hope I don't have this issue with the next upgrade.

---

