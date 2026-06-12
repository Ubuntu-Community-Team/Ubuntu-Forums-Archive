---
title: "Ubuntu 10.04 Choppy Audio"
date: 2010-07-24
forum: General Help
---

### Post by Narutokun on 2010-07-24
I just finished installing Ubuntu 10.04 as a dual boot with my Windows 7 partition. Everything seems to work great except for my sound. Sometimes there's no sound, and when there is sound, it's usually slightly choppy. Not choppy enough that it's unbearable, but it can get very annoying when listening to music. I am using a Turtle Beach Santa Cruz sound card if that helps. If anyone could help me fix this it would be great. Thanks in advance.

---

### Post by HPD2 on 2010-07-24
Try removing pulse audio and then reinstalling it. That fixed the choppy audio problem on my laptop.

---

### Post by Rodney9 on 2010-07-24
Thanks to LordRaiden

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Using alsamixer

* Type this into a shell
Code:

alsamixer

You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.

* To navigate around:
o Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen )
o
Up and Down Arrow Keys - Increase and decrease volume respectively.
o
Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey.

Saving Sound Settings
Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do
Code:

sudo alsactl store 0

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1. Many thanks to xpix for trying this out.-
______________

---

### Post by Narutokun on 2010-07-24
> **Rodney9 said:**
> Thanks to LordRaiden

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Using alsamixer

* Type this into a shell
Code:

alsamixer

You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.

* To navigate around:
o Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen )
o
Up and Down Arrow Keys - Increase and decrease volume respectively.
o
Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey.

Saving Sound Settings
Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do
Code:

sudo alsactl store 0

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1. Many thanks to xpix for trying this out.-
______________

What is this supposed to do for me if my sound does work but the choppyness is all that really messes it up. If I play something in Rhythmbox for instance, there isn't any sound playing unless I seek to the beginning of the audio track which then starts the music.

---

### Post by Narutokun on 2010-07-24
> **HPD2 said:**
> Try removing pulse audio and then reinstalling it. That fixed the choppy audio problem on my laptop.

I just attempted this, it seems to be the same as it was before I removed it and reinstalled it.

---

### Post by lidex on 2010-07-24
Is the santa cruz an add-in card? If so try disabling onboard audio device in bios.
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

