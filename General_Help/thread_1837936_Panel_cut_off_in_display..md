---
title: "Panel cut off in display."
date: 2011-09-02
forum: General Help
---

### Post by Underdosed on 2011-09-02
I have a Samsung Syncmaster, the native resolution is 1980 X 1080 / 67.5 kHz 60 Hz PP. I have it connected to the computer through an HDMI cable, it does 2 things when changing the resolution, it cuts out the panel completely or it cuts it in half; being that 1980 X 1080 isn't even selectable as an option I can see why this might happen. If someone could paste precisely what I need to throw into bash that would be great.

Version Post 9.10

---

### Post by searchfgold6789 on 2011-09-02
```
sudo dpkg-reconfigure -phigh xserver-xorg
```Might do it. You also might need drivers.

---

### Post by Underdosed on 2011-09-04
No dice and there are no Linux drivers for it.

---

