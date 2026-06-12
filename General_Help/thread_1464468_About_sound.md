---
title: "About sound"
date: 2010-04-28
forum: General Help
---

### Post by matrix75 on 2010-04-28
Dear community, first of all, thanks for the answers to come. And second: SORRY because English is not my mother tongue so, i`m sure i will make thousend mistakes!!! I´ve recently installed ubuntu on my computer which is an ACER AMD 64, 2gb RAM, at an Install Fest in Argentina. The people there helped me to install the controller for the ATI video card, i can see video, but i can´t listen to anything at all. ¿Can you help me to solve that problem?
I tried to run the search for controllers, but doesn´t find any one at all. Thanks in advanced.

---

### Post by dino99 on 2010-04-28
welcome to the community  :guitar:

you might check if your sound hardware is well recognized first, then tweak the settings. So goto system -- pref -- sound to see how it goes.

with synaptic, install gnome-alsamixer then goto apps -- sound -- gnome-alsamixer and uncheck if needed and adapt volume

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by towheedm on 2010-04-28
You installed an ATI [COLOR=Red]video card[/COLOR] but cannot sound?  Are you using an **[COLOR=Red]HDMI[/COLOR]** port on the card for sound or is the sound unrelated to the video card?

---

### Post by lidex on 2010-04-28
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

