---
title: "MythTV Video Issues"
date: 2006-06-11
forum: General Help
---

### Post by evertek on 2006-06-11
Hey, I'm working on a new setup using MythTV and Ubuntu. I've got it setup, but when I attempt to Watch TV the frontend is freezing and I have to reboot. I am using an older ATI TV Wonder (bttv driver), but I have it working great with xawtv.

I've rediected the frontend output to a file so I could check for errors. It seems to be crashing with: "NVP: Timed out waiting for free video buffers."

But earlier in the log I am getting a lot of "Failed to save cached image" errors when the theme loads. And a few "OSDImgCache, Error: Creating osdcache directory failed." after the audo device is opened.

A few things that may be useful. In xawtv I am unable to set the capture mode to overlay, I can only use grabdisplay. And I am also running on an older video card. Although those two problems may be related.

Any thoughts? Any help would be appreciated. Thanks.

---

### Post by evertek on 2006-06-12
Just a note.  Does anyone know what nVidia drivers EasyUbuntu installed.  I looked through the x log and it didn't seem as if the nvidia drivers were being loaded.  Maybe installing the real nvidia drivers would help this situation.

---

