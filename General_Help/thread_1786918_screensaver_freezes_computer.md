---
title: "screensaver freezes computer"
date: 2011-06-20
forum: General Help
---

### Post by Geraint on 2011-06-20
Hi
Running 11.04 on an old P3, 2D unity.
How can I disable screensaver through the terminal as it freezes if I open GUI screensaver app to turn it off.

Computer will not wake up from screensaver mode.

---

### Post by jerrrys on 2011-06-20
i believe the proper command is

killall gnome-screensaver

---

### Post by Geraint on 2011-06-21
> **jerrrys said:**
> i believe the proper command is

killall gnome-screensaver

Thanks that works.

I assume screensaver fails due to onboard graphics.

Need to run command after every bootup, any idea how to configure screensaver to none through the terminal?

regards

---

### Post by wildmanne39 on 2011-06-21
> **Geraint said:**
> Thanks that works.

I assume screensaver fails due to onboard graphics.

Need to run command after every bootup, any idea how to configure screensaver to none through the terminal?

regardsHi, here is a link on freezing.

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by jerrrys on 2011-06-21
sudo apt-get remove gnome-screensaver

sudo apt-get install xscreensaver

xscreensaver requires less resources

---

### Post by Geraint on 2011-06-21
Cheers sorted

---

