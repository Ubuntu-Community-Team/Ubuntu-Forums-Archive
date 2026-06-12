---
title: "Clipped sound in WMA file when played in Totem"
date: 2006-01-20
forum: General Help
---

### Post by Turin Turambar on 2006-01-20
There's one particular WMA video that I used to play it through Totem-xine with no problem at all.
I then reinstalled Ubuntu from scratch and probably messed something when installing Xine over Gstreamer and the sound  is now clipped.

However, gstreamer ver. of Totem CAN play that file with no prob. I did the reinstall, uninstall, configure... but with no success. Gstreamer uses WMA ver. 8 audio codec, while Xine uses a ffmpeg audio.

And where exactly is the Totem config file? I tried to edit totem_config in /home/.gnome2 and nothing happened.

Update:
I completely removed libxine1c2 and reinstalled it and now works great!!

---

