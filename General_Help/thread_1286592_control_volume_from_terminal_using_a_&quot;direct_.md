---
title: "control volume from terminal using a &quot;direct command&quot;"
date: 2009-10-09
forum: General Help
---

### Post by Gatemaze on 2009-10-09
Hello,

is it possible to change/control the volume with a single "command", something in the lines of $ volume +10

Many thanks

---

### Post by mac9416 on 2009-10-09
Perhaps amixer can help? These examples of what it can be used for are from its man page:

> EXAMPLES
       amixer -c 1 sset Line,0 80%,40% unmute cap
              will  set  the second soundcard's left line input volume to 80% and right line input to 40%, unmute it, and
              select it as a source for capture (recording).

       amixer -c 1 -- sset Master playback -20dB
              will set the master volume of the second card to -20dB.  If the master has multiple channels, all  channels
              are set to the same value.

       amixer -c 1 set PCM 2dB+
              will  increase  the  PCM volume of the second card with 2dB.  When both playback and capture volumes exist,
              this is applied to both volumes.

       amixer -c 2 cset iface=MIXER,name='Line Playback Volume",index=1 40%
              will set the third soundcard's second line playback volume(s) to 40%

       amixer -c 2 cset numid=34 40%
              will set the 34th soundcard element to 40%


Hope that helps.

---

### Post by Gatemaze on 2009-10-09
Yup, this will do... many thanks.

---

