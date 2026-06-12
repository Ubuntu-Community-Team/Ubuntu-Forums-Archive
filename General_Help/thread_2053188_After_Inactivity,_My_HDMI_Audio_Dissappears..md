---
title: "After Inactivity, My HDMI Audio Dissappears."
date: 2012-09-04
forum: General Help
---

### Post by fapestar on 2012-09-04
On my sound setings I have 4 option on output when I first boot up. HDMI AUdio (which is the one that gives me sound, because My LCD is hooked up to my Crossfired 6950 via HDMI, and My LCD is hooked up to my surround sound via Optical output. 

The second is digital output S/PDIF

The third Headphones

The fourth Analog Output. 

Now, after about 20 minutes of inactivity, HDMI dissapears and I cannot get any audio. 

How can I fix this?

---

### Post by fapestar on 2012-09-05
Here is a picture before the first HDMI audio dissappears

[ATTACH]223702[/ATTACH]

---

### Post by fapestar on 2012-09-05
prease....i even added a pic

---

### Post by fapestar on 2012-09-05
As you can see here...the HDMI is gone and I cant get my audio to work without restarting
[ATTACH]223732[/ATTACH]

---

### Post by TenPlus1 on 2012-09-06
This seems to be a problem with the Ati binary driver which some have reported as fixed in the latest beta, although here are a few tricks to re-enable to audio without updating:

1. Change screen mode to something different and then back again, it will bring back audio.

2. in Terminal type:  aticonfig --acpi-services=off     to disable suspend on graphics card, aticonfig --acpi-services=on    turns it on again.

3.  Changing to a different tty using CTRL + ALT + (F1 to F6) then changing back to main desktop using CTRL + ALT + F7 (or F8 for some) will reset screen and audio.

---

### Post by fapestar on 2012-09-07
THanx bro, that first one worked.

---

