---
title: "Karmic problems with audio"
date: 2009-11-06
forum: General Help
---

### Post by Pauly BC on 2009-11-06
I have two challenges with the audio in Karmic that are not hardware related because they don't happen in Windows.

1. When the sound is muted, every time a program would play a sound, a very loud pop sound is heard. Normally with audio muted you should expect to hear nothing, but in fact you get very very loud pops every now and then.

2. When playing MP3's, there is a very annoying high-pitched squeaking added to the sound. Again the same file in Windows and my MP3 player does not have the issue. It sounds like the squeak from a cricket, only instead of 'squeak' it is just 'eeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee'

Ugh

I have an onboard Realtek 883 audio, and my video is ATI 3850 HD with the driver activated.

---

### Post by pjbgravely on 2009-11-06
Mine has the pops, very annoying but it seems to be ok.

The squealing I found was caused by the levels set too low. I had to use alsamixer in a terminal to raise all the levels and the problem went away, well at least for now.

Paul

---

### Post by Pauly BC on 2009-11-09
bump

---

### Post by michy99 on 2009-11-09
The popping is caused by a power-saving setting. Open /etc/modprobe.d/alsa-base.conf for editing.```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```Find the line that reads```
options snd-hda-intel power_save=10 power_save_controller=N
```It's probably the last line. Put a # at the beginning of the line to comment it out. Save and reboot.

Sorry, I don't know about the second issue.

---

### Post by Pauly BC on 2009-11-10
Michy99 was correct that the pops were related to power saving and easily cleared, though the solution seems bass-ackwards. When the sound is muted, you need to disable power saving in order to stop it from popping even though it's muted. Hmm.

The squeaking was resolved by opening alsamixer from terminal and adjusting the speaker volumes through its little utility.

Those are solved but now the mp3 player does not use my subwoofer and Amarok freezes at the splash screen.

grrr.
death by a thousand paper cuts so far!

---

