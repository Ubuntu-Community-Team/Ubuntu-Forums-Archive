---
title: "No video in Skype"
date: 2011-11-19
forum: General Help
---

### Post by iosrcr on 2011-11-19
Hi all,
My Genius Eye 312 webcam works fine in cheese and camorama
but I can't see my video in Skype.
I have Kubuntu 11.10 x64
skype beta version 2.2.0.35 (downloaded from skype.com)
I go to options/video devices select my webcam (there's only one) "USB Camera (093a:2622)(/dev/video0)" and click on test button. There's a black screen and no light on webcam (light was on when using cheese).
I am new to Ubuntu. And sorry for bad English.
thanks

---

### Post by dabl on 2011-11-19
I forget where I got this script a year ago or so

```
#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
exit 0

```

Note that you'll need to have v4l installed.

Just name the script "skypelauncher.sh" or something like that. Save it in your user's home folder, then in a user terminal

```
chmod +x skypelauncher.sh
```

In your skype icon, which I park on the panel, you can right-click and choose "icon settings", choose the "Application" tab, and on the Command line put "/home/username/skypelauncher.sh".  Then it should launch with video enabled.

---

### Post by iosrcr on 2011-11-20
Thank you verrrrrry much

---

