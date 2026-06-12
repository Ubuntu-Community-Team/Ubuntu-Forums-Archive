---
title: "Pulseaudio annoyance"
date: 2011-07-25
forum: General Help
---

### Post by hambone79 on 2011-07-25
In my home office I have two computers sharing a set of speakers. I have a line running from my Windows computer to line-in on my Linux computer. I also have a microphone attached to the Linux computer that I used for video chat. Now here is my issue:

1. Pulseaudio will not let me use both line-in and microphone as input. It's one or the other.
2. I can't hear the sound on line-in unless I load the loopback module.
3. I can't unload the loopback module when I video chat without rebooting the whole computer.

These problems are a major inconvenience for me so I would like to see if anyone else has found a way around this. Basically I would just like a mixer that lets me keep both inputs running but gives me mute/loopback controls for each one. At this point in time, the only way I see to fix it is to run audio in the opposite direction...back into the Windows box.

---

### Post by enimeizoo on 2011-07-26
Did you try to uninstall pusleaudio?
It solved lots of audio problems, here...

---

### Post by hambone79 on 2011-08-13
I don't think it should be necessary to uninstall pulseaudio to fix this problem. This is 2011...a sound system should have the capability of mixing several sources at once instead of forcing me to pick one at time.

---

### Post by raja.genupula on 2011-08-13
[http://ubuntuforums.org/showthread.php?t=1498341](http://ubuntuforums.org/showthread.php?t=1498341)


[http://ubuntuforums.org/showthread.php?t=1402034](http://ubuntuforums.org/showthread.php?t=1402034)

---

### Post by hambone79 on 2011-08-14
Well, looks like I have to install ALSA. Why does Ubuntu even bother with Pulseaudo? It has caused me nothing but problems since it was added several releases ago.

---

