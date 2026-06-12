---
title: "skype and the mic."
date: 2012-07-02
forum: General Help
---

### Post by PNY on 2012-07-02
Hi there.

sound recorder is working on my linux machine and i can record and playback a file. 
skype however is not able to use the mic on this machine and so the machine has the problem of no skype.

The question is, how do we get skype to use the mike correctly?

---

### Post by Rodney9 on 2012-07-02
Fix internal mic for use with Skype

[http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol](http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol)

```
sudo apt-get install pavucontrol
```


PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

Thanks To ZekeGraal


Rodney

---

### Post by Rebelli0us on 2012-07-02
It should work, just make sure that mike is not muted in Input / Sound Preferences.

---

### Post by PNY on 2012-07-02
cool.
installed this tool this afternoon

checked it again now and no joy

the mic just not pickin up sound

---

