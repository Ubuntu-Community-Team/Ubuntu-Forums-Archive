---
title: "Missing Volume Control"
date: 2010-01-11
forum: General Help
---

### Post by huviduc on 2010-01-11
The volume control app has disappeared from the panel. I have checked under the "add to panel" option the there is nothing for volume control or similar. I do have the notification area there but there and ive removed and re-added it. I tried running "gnome-volume-control-applet" in terminal and it says it is not installed. I can control the volume with my remote and with the knob on my keyboard. But it seems to have vanished from the notification area.

---

### Post by mocoloco on 2010-01-12
Strange.  I know that in Karmic the volume control is no longer an independent applet on the panel and instead runs in the systray or "notification area" if you will.  Looks like it loads in the startup applications.

But if I kill it I can run gnome-volume-control-applet and it comes back.  A "which gnome-volume-control-applet" reveals
```
/usr/bin/gnome-volume-control-applet
```

If you don't have it there maybe you need to reinstall whatever source package puts it there?

---

### Post by huviduc on 2010-01-12
Any idea what i would re reinstalling? I tried installing gnome-volume-control-applet but it doesnt exist. I also tried searching through synaptic but didnt see anything.

---

### Post by michy99 on 2010-01-12
It is in the gnome-media package. You should know that in Karmic, the Gnome volume control only woks with pulse-audio, so if you have removed pulse-audio like I have, you will have to use alsa mixer to control the volume.

---

### Post by warfacegod on 2010-01-12
This worked for me:

[http://ubuntuforums.org/showthread.php?t=1378372&highlight=missing+master+volume]("http://ubuntuforums.org/showthread.php?t=1378372&highlight=missing+master+volume")

---

### Post by huviduc on 2010-01-12
I havent removed pulse audio so i will try reinstalling gnome-media and see if it comes back

---

