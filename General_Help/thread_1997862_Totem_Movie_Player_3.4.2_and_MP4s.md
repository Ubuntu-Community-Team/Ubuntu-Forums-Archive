---
title: "Totem Movie Player 3.4.2 and MP4s"
date: 2012-06-05
forum: General Help
---

### Post by Sir Rodness on 2012-06-05
Not sure what happened since I moved to 12.04, but now my movie player doesn't seem to play all my MP4 files that it use to play. It does play some of them, but there some it won't play at all for reasons unknown. Anyone else notice this type of issue?

---

### Post by hansdown on 2012-06-05
hi Sir Rodness.

Do you get any error popups?

---

### Post by Sir Rodness on 2012-06-05
> **hansdown said:**
> hi Sir Rodness.

Do you get any error popups?

Nope, it just shows playing 0:00/0:00 at the bottom. I thought the files might of gotten corrupted some how, but they all play in VLC. Well I guess that's not fair since VLC will play pretty much anything. :)

---

### Post by hansdown on 2012-06-05
Vlc does have a couple plugins that totem may not have.

---

### Post by mc4man on 2012-06-06
likely the result of this bug 
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)

The best fix by far  is to rebuild the ugly plugin source with the patch I supplied in comment 33, a lesser 'workaround' is to move libgstvideoparsersbad.so to a .bak as shown in comment 22 noting arch

---

### Post by Sir Rodness on 2012-06-08
Thanks mc4man, I tried the workaround and that's good enough for me. Any other mishaps I'll just use VLC. :)

---

