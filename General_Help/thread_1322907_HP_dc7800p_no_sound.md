---
title: "HP dc7800p no sound"
date: 2009-11-11
forum: General Help
---

### Post by mikeglover on 2009-11-11
I have got ubuntu 9.10 on a HP dc7800p.
It appears that the on board sound has been recognised but the internal speaker does not work.
Has anyone else had this problem?
I have used Windows XP on this machine so I know that it does work and not a hardware fault.

---

### Post by mikeglover on 2009-11-17
[I]bump
[/I]
I since found that the sound card I have is an intergrated Intel HDA.
Anyone been able to get internal sound working on these?

---

### Post by John Bean on 2009-11-17
Don't know about Karmic, but in Jaunty the fix is to edit /etc/modprobe.d/alsa-base.conf and add the line "options snd-hda-intel model=laptop" to the end.

---

### Post by P4man on 2009-11-17
Try the above suggestion. In case you dont know how to edit that file, open a terminal and copy paste this command:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf 
```

You may also want to confirm and subscribe to this bug report:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/472864](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/472864)

---

### Post by mikeglover on 2009-11-17
tried that but it didn't work.

I have kind of found a workround. If I remove pulseaudio package it works. But I lose volume control :(
But has my friend says, its like using a sledge hammer to hit a nail.

---

### Post by P4man on 2009-11-17
try reinstalling pulseaudio and also install ```
pavucontrol
```
Then try changing the settings in applications > sound and video > pulseaudio volume control. Specifically check the last tab.

---

### Post by mikeglover on 2009-11-17
Brilliant it works :D

---

