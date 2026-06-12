---
title: "No sound again after upgrade to 10.04"
date: 2010-04-30
forum: General Help
---

### Post by uMany on 2010-04-30
Hi,

After upgrade to Lynx from Karmic my machine (sony vaio F-series laptop  i7) I lost the sound. Before upgrading I did not have input sound but  output.

Here is my uname and everything:
uname -a
Linux umany 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC  2010 x86_64 GNU/Linux
umany@umany:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
umany@umany:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
umany@umany:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 275

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID b

Thanks in advance

Happy upgrade for everyone

---

### Post by UrbanGorilla on 2010-04-30
You've probably tried this, but I thought I had no sound, and then found that for some reason the sound is muted by default.

---

### Post by dino99 on 2010-04-30
add this line to /etc/modprobe.d/alsa.conf

options snd-hda-intel model=auto

if it does not work, you have to find the exact model from alsa project

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

into synaptic install gnome-alsamixer and tweak it (apps system tools)

---

### Post by uMany on 2010-05-13
Hi folks,

I've been looking for more than a week for a solution to my problem with the input sound and nothing.
Thanks for your advice but none had worked.
Any other Idea?
Thanks in advance

---

