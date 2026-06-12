---
title: "Audio full of static and too low"
date: 2010-10-19
forum: General Help
---

### Post by schwim on 2010-10-19
After upgrading from .04 to .10, My audio is full of static.  I've also noticed that it is at a lower volume even with the sliders maxed than if I boot into Windows.  It used to be that I could leave the speakers alone and booting into either gave the same level of volume.  Now, I have to max out the volume on the physical speakers to get a similar level of volume to my Windows install.

To describe the sound problem, it sounds as if  one of the sliders has been pushed too far and it's distorting the sound.  I've tried it across several applications(rhythmbox, browser),  and all audio is like this.

I've looked at the audio settings on the dock panel, but nothing seems  amiss(and in fact doesn't leave much room for manipulation).

I have tried the fix listed in the sticky found in the general category:

load-module module-udev-detect tsched=0 
but the problem persists after reboot.

I've waited, hoping that an update would resolve the issue, but over a week has passed and I'm still using Windows due to the sound problem in my Ubu install.

Any help would be greatly appreciated.

---

### Post by schwim on 2010-10-19
Anyone?

---

### Post by schwim on 2010-10-20
Bumping to get a chance to witness the power of linux.

---

### Post by schwim on 2010-10-22
Bumping to revel in the fantastical helpfulness that defines open source communities.

---

### Post by schwim on 2010-10-23
Bumping to gape in awe of the sheer power of FOSS

---

### Post by Volens on 2010-10-23
You may have already tried this, but try typing
```
alsamixer
```
into a prompt and mess with those settings/sliders. Sometimes I've had more luck with those.

---

### Post by schwim on 2010-10-23
Thanks very much for your help.  I tried the alsamixer in the terminal, but if I turn any down to the point that the static disappears, I have to turn the speakers to the max to hear anything at all.  Also, regardless of which I manipulate, all bars seem to be directly tied to the master control.  For instance, if I turn down front, the sound control on the taskbar moves down in correlation.  If I move "side" or "back", the same happens, so if I turn any down to get rid of the static, as soon as I close alsamixer and turn the volume up via the taskbar, all bars are maxed out again, making alsamixer ineffective, in my case.

---

