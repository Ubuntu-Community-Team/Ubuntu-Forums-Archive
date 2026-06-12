---
title: "update but no sound"
date: 2010-05-08
forum: General Help
---

### Post by nush on 2010-05-08
hi
i am using ubuntu 9.10.
yesterday i received an auto update. dont know if this has caused my problem but today i have no sound at all from my laptop.
everything seems to be working as though sound is working but i get no out put.
any suggestions as to what might be the problem would be welcome.
thanks nush

---

### Post by rebtal on 2010-05-08
Same problem on 10.04. Autoupdate yesterday on a Dell latitude D600. No sound after reboot...

SOLVED : I was not present in the audio group (don't know why) when I do
fgrep -ie 'audio' /etc/group

so : 
sudo adduser MY_USERNAME audio

See [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by lidex on 2010-05-08
Check for muted levels in alsamixer. ```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by nush on 2010-05-09
> **lidex said:**
> Check for muted levels in alsamixer. ```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.



thanks
this worked for me, but even with the volume levels high the output is lower than normal. not sure why updates need to alter my other settings, it one of the reasons i dont use ms windows any more.
nush

---

