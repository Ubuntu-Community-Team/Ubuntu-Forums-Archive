---
title: "Video playback very fast with gtk-recordmydesktop"
date: 2010-08-28
forum: General Help
---

### Post by James2k on 2010-08-28
I've been hunting around for some screen capture software in Ubuntu, for future screencasts and out of the handful I've tried I've gone with gtk-recordmydesktop. After initial problems with recording quality, I have managed to get everything working but have noticed that on playback of any captured video, is played back at a crazy speed, the frame rate is not the issue as it is on the default 15 FPS setting but still the play back is very fast.

I noticed before my tweaking that playback was normal speed, but the quality was garbage, and I found that this was because of Compiz being enabled, and I have to run gtk-recordmydesktop with "Encode on the fly" and "Full shots at every frame" enabled in order for the video playback to not be all cut up, however ever since encoding on the fly has been enabled, this has caused playback to be hilariously fast.

Does anyone know a way to fix this issue?

I'm running Ubuntu 10.04 with Compiz enabled. With an nVidia GPU (8200 M)

---

### Post by James2k on 2010-08-30
I've moved away from gtk-recordmydesktop and found that xvidcap suits my machine better.

---

