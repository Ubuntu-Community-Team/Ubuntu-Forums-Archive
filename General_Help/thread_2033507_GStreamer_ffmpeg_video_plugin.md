---
title: "GStreamer ffmpeg video plugin"
date: 2012-07-26
forum: General Help
---

### Post by izombie666 on 2012-07-26
I am not able to install GStreamer ffmpeg video plugin.  I receive and error that says:

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

I am using 12.04.  Any suggestion on what is causing this conflict?

Thanks

---

### Post by mc4man on 2012-07-26
Maybe you have some outside or ppa packages instelled, maybe something else.

open a terminal & run this, copy & post everything from the terminal
```
sudo apt-get -s install gstreamer0.10-ffmpeg
```

---

