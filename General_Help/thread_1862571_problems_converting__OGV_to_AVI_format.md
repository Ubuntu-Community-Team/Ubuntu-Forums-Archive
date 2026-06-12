---
title: "problems converting  OGV to AVI format"
date: 2011-10-16
forum: General Help
---

### Post by larry3d on 2011-10-16
[B][SIZE=2]mencoder -idx filename.ogv -ovc lavc -oac mp3lame -o filename.avi
[COLOR=Red]
Too many audio packets in the buffer: (4096 in 4096 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  266.678 kbit/s  (33334 B/s)  size: 4742428 bytes  142.267 secs  1946 frames

Audio stream:    7.963 kbit/s  (995 B/s)  size: 142116 bytes  142.785 secs[/COLOR]
[COLOR=Black]

[SIZE=3][COLOR=Blue]any ideas how can i fix this problem because i only converting just few seconds of any recordings than stops by no finishing 


[/COLOR][/SIZE][/COLOR][/SIZE][/B]

---

### Post by larry3d on 2011-10-16
i also got this 

Pos: 119.9s   1646f (100%) 383.86fps Trem:   0min   9mb  A-V:-0.140 [684:7]

1 duplicate frame(s)!
Pos: 120.1s   1648f (100%) 384.06fps Trem:   0min   9mb  A-V:-0.087 [683:7]

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  683.163 kbit/s  (85395 B/s)  size: 10253135 bytes  120.067 secs  1648 frames

Audio stream:    7.963 kbit/s  (995 B/s)  size: 120016 bytes  120.581 secs


PLEASE SOMEONE HELP ME

---

### Post by andrew.46 on 2011-10-27
Would you consider using FFmpeg rather than MEncoder? FFmpeg development has easily outstripped work on MEncoder which is slowly becoming defunct. Can you also give a few details about your conversion, is it for a special device or do you wish to change the audio or video codecs?

---

