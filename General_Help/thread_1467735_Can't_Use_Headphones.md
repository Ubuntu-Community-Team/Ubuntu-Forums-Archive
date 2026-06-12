---
title: "Can't Use Headphones"
date: 2010-05-01
forum: General Help
---

### Post by Hman242 on 2010-05-01
Sound in Ubuntu 10 will only play from the speakers on the laptop, not out of the headphones plugged in through the headphone jack. Help would be appreciated.

---

### Post by Hman242 on 2010-05-01
*Bump To Front Page*

---

### Post by trig on 2010-05-01
i have something similar and a  little stange, i have no sound in the front jacks but i do in the back.

---

### Post by Hman242 on 2010-05-01
I fixed it. All I had to do was click the sound icon, then click **Sound Preferences. **From there I went to the **Output** tab and clicked on the drop-down arrow. I changed it from **Analog Speakers** to **Analog Output**.

I really need to try and fix things before I complain.

---

### Post by Aearenda on 2010-05-01
Try running 'alsamixer' in a terminal - there are probably extra settings not visible on the GUI. On my system, I had to turn headphone jack sensing on. To save the settings, do ```
sudo alsactl store
```

---

### Post by facejumphead on 2010-05-01
The fix above didn't work for me. When I changed "Analog Speakers" to  "Analog Output", then I don't get sound out of either the speakers or  the headphones.

It also seems worth noting that in alsamixer, there is a column labeled  headphones with the volume set to 0 that is not muted, but I can't adjust the volume.

---

### Post by dino99 on 2010-05-01
depend on your chipset or card it may be different issues, but

install paprefs and gnome-alsamixer (tweak its settings --> :  apps --> sound)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by facejumphead on 2010-05-01
I tried installing gnome-alsamixer, but the headphones don't appear there, so I couldn't tweak anything.

I also went through the troubleshooting page, but didn't see anything related to my problem.

---

### Post by facejumphead on 2010-05-01
Bump. Is there anything I can run that will give hardware specs to help out? I'm going to need to go back to an earlier version of Ubuntu if I can't fix this. :(

---

### Post by lidex on 2010-05-01
> **facejumphead said:**
> Bump. Is there anything I can run that will give hardware specs to help out? I'm going to need to go back to an earlier version of Ubuntu if I can't fix this. :(

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by facejumphead on 2010-05-02
I just figured it out. I was had the wrong line added to my /etc/modprobe.d/alsa-base.conf file. I saw the asus model in that text file that came with the update script, so I was using

```
options snd-hda-intel model=asus
```but I needed this:
```
options snd-hda-intel model=g71v probe_mask=1
```

---

