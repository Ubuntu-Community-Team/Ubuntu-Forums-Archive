---
title: "how do I search for drivers for my monitor?"
date: 2009-11-27
forum: General Help
---

### Post by Gatorade on 2009-11-27
I'm having issues with the display on my toshiba portege laptop.

I'm guessing its got to do with Ubuntu 9.04 not detecting the monitor.
when I check display preferences its saying monitor : unknown.

I can only get 800 x 600 resolution and there's about an inch of space around the whole screen thats black.

---

### Post by carl.davis on 2009-11-27
You probably want to look for drivers for your video card, not your LCD.

---

### Post by Gatorade on 2009-11-27
I installed the trident drivers for my video card from the synaptic package manager , but I still can't get it to work right.

---

### Post by carl.davis on 2009-11-27
After you installed the drivers did you do a reboot or restart X?

---

### Post by Gatorade on 2009-11-28
yes , I did a restart.

I asked in another forum and was told I may need to configure it manually.

---

### Post by carl.davis on 2009-11-28
Now that you have the drivers installed you could try to reconfigure X with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by WinterWeaver on 2009-11-28
Does the drivers not show up when you go to: System >> Administration >> Hardware Drivers

---

### Post by Gatorade on 2009-11-28
I got it working .

I asked for help in another forum and the guys there wrote a config file for me and I just had to copy it and paste it in , rebooted and the option for the larger display was there.:D

---

