---
title: "Dual Monitors"
date: 2009-08-14
forum: General Help
---

### Post by scouser73 on 2009-08-14
Here goes, I have dual monitors set up on Ubuntu Jaunty, I have an nVidia GeForce 6200 graphics card. One monitor is plugged into the VGA slot and the other is plugged into the DVI slot.

I have read this article [[COLOR="Red"]**Ubuntu Dual Monitors**[/COLOR]]("http://www.ubuntugeek.com/dual-monitors-with-nvidia.html") and have it working but every time that I start the PC, only one monitor will show up.

I can't restart X by ctrl, alt & backspace and I know that function has been disabled in Jaunty.

Where am I going wrong?

---

### Post by wojox on 2009-08-14
Do you have NVIDIA X Server Settings installed? If not open synaptic, search nvidia and mark for installation nvidia-settings and configure that way.

---

### Post by realzippy on 2009-08-14
..the article is 2 years old...meanwhile you can setup TwinView
with nvidia-settings..

type:

**gksudo nvidia-settings**

when setup desired settings,hit the
"save to X configuration file"

---

### Post by scouser73 on 2009-08-14
Yeah, I have Nvidia X settings installed, each time that I have to reapply it, it tells me to restart x again, and it's disabled.

---

### Post by realzippy on 2009-08-14
Open the nvidia-settings with

**gksudo nvidia-settings**

when setup desired settings,hit the
"save to X configuration file"

...otherwise your setup will be lost.

---

### Post by soapBAR2 on 2009-08-14
> **scouser73 said:**
> Yeah, I have Nvidia X settings installed, each time that I have to reapply it, it tells me to restart x again, and it's disabled.

You're not saving the changes to your xorg.conf. This is because you're not running nvidia-settings as root,

```
gksudo nvidia-settings
```

or you're not clicking the "Save To X Configuration File" (above the quit button), or you're not saving it to /etc/X11/xorg.conf. You can check by backing up your /etc/X11/xorg.conf to /etc/X11/xorg.conf.backup , and then running 

```
diff /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
```

after you've set the server up. If the diff returns nothing, then it's not saved (in which case you have a very weird problem).

---

### Post by scouser73 on 2009-08-14
Thankyou, having researched a few tutorials on setting up dual monitors, not once did it say that I needed to run the nvidia settings as root. Your quick and simple advice has ended about 10 hours of brain wracking.

---

