---
title: "Sloooow 3d-acceleration"
date: 2006-03-01
forum: General Help
---

### Post by Wolfbite on 2006-03-01
I just found out that my 3d acceleration isn't worth a damn. I got a Radeon 9800 128mb card, and I've installed the latest official ATI linux drivers. When I type glxgears -printfps in my terminal, I get:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
872 frames in 5.4 seconds = 161.708 FPS
840 frames in 5.5 seconds = 153.686 FPS
840 frames in 5.6 seconds = 149.485 FPS
840 frames in 5.5 seconds = 152.250 FPS
840 frames in 5.5 seconds = 151.875 FPS

```

I suspect the fps should be much, much higher, considering the extremely low fps I experience when I load up WoW (1 frame every 2 seconds or something). Also, I have no clue what XFree86-DRI is, but anything missing never sounds good. Could I have some help, please? :)

---

### Post by mlind on 2006-03-01
see if this helps any
[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)

---

