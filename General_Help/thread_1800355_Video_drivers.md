---
title: "Video drivers"
date: 2011-07-08
forum: General Help
---

### Post by Elitenoname on 2011-07-08
Ok I think I know what is happening, in my laptop there it the Intel Hd graphics and then there is an Nvidia Ion nextgen graphics card and when I go to activate the Nvidia drivers and restart my computer I lose my GUI. I can only see 1 line of the errors and it is stating that the Intel graphics errored out and failed to load the GUI. I am a bit lost on how to fix this.

I have done
```
sudo nvidia-xconfig
```
then restarted the service and restarted the computer

and that is about all i really know how to do off the top of my head.

---

### Post by pqwoerituytrueiwoq on 2011-07-08
```
lspci | grep VGA
```
lets find out if you are running a nvidia or intel gpu

---

### Post by Elitenoname on 2011-07-08
well i get

```
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
04:00.0 VGA compatible controller: nVidia Corporation Devices 0a76 (rev a2)
```

---

### Post by pqwoerituytrueiwoq on 2011-07-08
if you can run compiz without the nvidia driver you are using the intel gpu
nvidia is probably a hdmi port or other second monitor port

---

### Post by Elitenoname on 2011-07-08
Ok then how to I select the card I want to use and make it so my GUI will work and not error out?

also this is a laptop (asus 1215n) if that help any

---

### Post by wildmanne39 on 2011-07-09
> **Elitenoname said:**
> Ok then how to I select the card I want to use and make it so my GUI will work and not error out?

also this is a laptop (asus 1215n) if that help any
Hi, did you have any problems before you activated the driver for the nvidia card? if not you can just deactivate it and you should be back to your intel card.

---

