---
title: "Video Playback is a Black Screen"
date: 2011-09-07
forum: General Help
---

### Post by Kissell on 2011-09-07
I'm using Ubuntu 11.04 64-bit on a laptop with an ATI Radeon HD 3200 graphics card.  

When I play a video it works, then I play another video, it works...  but eventually I'll play a video and I'll hear audio but get no video, just black inside the player.  I try several players, mplayer, vlc, ect...  they're all black.  

Switching viewports ALT-F1, then back to ALT-F7 doesn't fix it.  Logging out and back in doesn't fix it.  I have to completely reboot to fix it.  

I am using the restricted drivers downloaded via the ubuntu additional drivers menu item.   I'm using compiz and unity 3D.

---

### Post by roman.lange on 2011-09-08
Edit: found a solution to my problem. I opened "gstreamer-properties" in a terminal and in the video tab, I changed the setting to X window system (no Xv) in default output.

I face the exact same problem. Does anyone know what should be done to solve this?

---

### Post by Linux_junkie on 2011-09-08
> **Kissell said:**
> I'm using Ubuntu 11.04 64-bit on a laptop with an ATI Radeon HD 3200 graphics card.  

When I play a video it works, then I play another video, it works...  but eventually I'll play a video and I'll hear audio but get no video, just black inside the player.  I try several players, mplayer, vlc, ect...  they're all black.  

Switching viewports ALT-F1, then back to ALT-F7 doesn't fix it.  Logging out and back in doesn't fix it.  I have to completely reboot to fix it.  

I am using the restricted drivers downloaded via the ubuntu additional drivers menu item.   I'm using compiz and unity 3D.

Is the DVD with the black screen an encrypted disk? Have you downloaded the libdvdcss2  file? If you haven't installed it type the following command

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

