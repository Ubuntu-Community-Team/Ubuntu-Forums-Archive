---
title: "Default sound card 9.10 ..."
date: 2010-02-04
forum: General Help
---

### Post by kantu on 2010-02-04
I recently installed Ubuntu 9.10 , i was using Slackware before , in that i added a sound file in /etc/modprobe.d/ directory
as 
```
alias snd-card-0 snd-ca0106
alias sound-slot-0 snd-ca0106
options snd-ca0106 index=0
alias snd-card-1 snd-hda-intel
alias sound-slot-1 snd-hda-intel
options snd-hda-intel index=1

```
By this my SoundBlaster Card was always default but now if i add the same file still no difference is there , and it does not remember the settings also every settings will be re-set.
Where should i configure it ???

---

### Post by kostkon on 2010-02-04
> **kantu said:**
> Where should i configure it ???
System &#8594; Preferences &#8594; Sound

---

### Post by kantu on 2010-02-04
i tried it .. that s what i told its not remembering the settings when i reboot Volume will be Mute , sound card will be hda-intel not ca0106(SB) so now theres no sound in mpd :(

---

### Post by stoneage on 2010-02-04
You could try this, but it is probably out of date now:-
[http://ubuntuforums.org/showthread.php?t=922860&highlight=sound](http://ubuntuforums.org/showthread.php?t=922860&highlight=sound)

I think now the relevant file is /etc/modprobe.d/alsa-base.conf

---

### Post by kantu on 2010-02-04
i modified both files i.e alsa-base and sound now default is SB card

---

