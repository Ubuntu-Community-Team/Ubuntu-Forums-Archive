---
title: "Video player that works for wmv or avi files"
date: 2009-07-19
forum: General Help
---

### Post by oldtraveler on 2009-07-19
On my recent installation of ubuntu 9.04 the native media player is Movie Player.  When I try to play either wmv or avi files there is no audio, and the video is either blank or moves very slowly and then stops.  Is there a better player available?  Even vlc plays OK, but no audio.

---

### Post by t0p on 2009-07-19
Have you installed the non-free codecs?  You can do this by typing into the terminal

```
sudo apt-get install ubuntu-restricted-extras
```

**EDIT:** On re-reading the OP, I see you get the video but no audio.  So I guess you *don't* need the codecs.  Do you?

---

### Post by oldtraveler on 2009-07-19
Re-booting solved the sound issue for both Movie Player and vlc.

Have installed the non-free codecs also.  Thank you.

---

