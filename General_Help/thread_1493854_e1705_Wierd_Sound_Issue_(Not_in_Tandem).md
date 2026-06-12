---
title: "e1705 Wierd Sound Issue (Not in Tandem)"
date: 2010-05-26
forum: General Help
---

### Post by dh04000 on 2010-05-26
When I installed Lucid, it created a sound problem. I have a Dell Inspiron e1705. The issue is the subwoofer and the other two speaker in my system do not work in tandem. In prior Ubuntu releases I would fix this problem by making the volume up and volume down button control but the subwoofer and the two speakers (Master+PCM). But with Lucid, I don't seem to have the option to set up my audio due to the "simplification" of the audio bar. I downloaded the Gnome ALSA mixer from the repository, but it doesn't have the function I need either.

Any idea guys? Something else I can DL to allow me to get my audio to work? I'm loving everything else in this release, please down let me down!


Oh, I've been on ubuntu for 2 years, so I'm not retarded, feel free to give me complicated instruction, but GUI ones are preferred(I remember them in the long run). Thanks.

---

### Post by dh04000 on 2010-05-26
Bump

---

### Post by dh04000 on 2010-05-26
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948)

This appears to describe the bug.

There appears to be a bug fix. Can someone translate this into instructions I can follow?

---

### Post by dh04000 on 2010-05-26
It really sucks to be an audiophile and not have good sound...

---

### Post by dh04000 on 2010-05-26
Need some help guys. Used to be able to fix this myself, but the audio center had to be messed with. Now I'm lost. Please help!

---

### Post by dh04000 on 2010-05-26
Bump

---

### Post by A990 on 2010-05-26
I'm having the same problem on the same type of laptop.

BUMP!

---

### Post by JoelOl75 on 2010-05-26
sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
You will find those lines near the bottom of the file:

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

So, add theses lines BEFORE:


[Element Master]
switch = mute
volume = ignore
and these lines AFTER:


[Element LFE]
switch = mute
volume = ignore
You should finally have:


[Element Master]
switch = mute
volume = ignore

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element LFE]
switch = mute
volume = ignore


Save and quit. Then restart (restarting Pulseaudio isn't enough).

---

### Post by dh04000 on 2010-05-27
Now I don't hear anything at all.

---

### Post by dh04000 on 2010-05-27
Ok, I fooled around with the gnome ALSA mixer, and if I set the Master and LFE at 2/3, then your solution works pretty good. If there anyway to make Master and LFE to increase and decrease in tandem with PCM?

It appears that on my system:

PCM: total volume
Master: Speaker volume
LFE: Subwoofer volume.



Thanks for the help man, I really appreciate it. Rocking to jams as I type! :)

---

