---
title: "Mencoder question."
date: 2006-04-15
forum: General Help
---

### Post by jimmygoon on 2006-04-15
So I'm learning how to use Mencoder and I have (another) question for everyone here... I have googled... and googled... to no avail... so I ask of thee...

```
mencoder dvd://1 -dvd-device /dev/dvd -oac mp3lame -ovc lavc -xvidencopts pass=1:bitrate=687:bitrate=5000 -vf scale=720:-2 -o "lc2e_trial.avi" 
```
This is successful. It works perfectly.

```
mencoder dvd://2 -dvd-device /dev/dvd -oac mp3lame -ovc lavc -xvidencopts pass=1:bitrate=687:bitrate=5000 -vf scale=720:-2 -o "lc2e_trial.avi" 
```
This code is identical except for the fact that it rips a different title off of the dvd. When this runs... I'm given this junk: > <snip>

Pos:   9.6s    290f (31%) 29.58fps Trem:   0min   0mb  A-V:0.055 [235:0]
Too many video packets in the buffer: (4096 in 8269805 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos:   9.6s    291f (31%) 29.44fps Trem:   0min   0mb  A-V:0.055 [235:0]
Too many video packets in the buffer: (4096 in 8269805 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos:   9.6s    292f (31%) 29.49fps Trem:   0min   0mb  A-V:0.055 [234:0]
Too many video packets in the buffer: (4096 in 8269805 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos:   9.7s    293f (31%) 29.35fps Trem:   0min   0mb  A-V:0.055 [234:0]
Flushing video frames
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  234.046 kbit/s  (29255 B/s)  size: 283088 bytes  9.676 secs  293 frames

Audio stream:  128.000 kbit/s  (16000 B/s)  size: 15744 bytes  0.984 secs

</snip>


Video *seems* to be okay... but there is no audio :(. Any help would be appreciated

---

### Post by jimmygoon on 2006-04-15
small bump.

---

