---
title: "Compizconfig missing Display Settings options"
date: 2011-09-14
forum: General Help
---

### Post by ms801000 on 2011-09-14
Hi,

I'm running the latest version of Ubuntu on an e-machine er1401. Managed to get most things working, sound over HDMI, shutdown without hanging etc but I keep seeing solutions posted that involve changing the options in CompizConfig Settings Manager > General > Display settings tab

I have CompizConfig Settings Manager installed but when I go into the Display Settings Tab I dont see refresh rate options or Sync to vBlank... just the Overlapping Output Handling option (set to Smart mode) and Detect Outputs (ticked) with 640x480+0+0 in the Outputs box. No other options.

Have I miss-installed something or do I need to enable an option somewhere? Any help is appreciated!

Matt

---

### Post by Frogs Hair on 2011-09-14
Welcome to the forums !

I have the same options displayed with all the extra plug-ins installed . If the setting was there it could have been moved or removed .

---

### Post by ms801000 on 2011-09-14
Thanks for checking. If you dont have the options either do you know how to change the Sync to vBlank and Refresh Rate settings?

Matt

---

### Post by ajgreeny on 2011-09-14
> **ms801000 said:**
> Thanks for checking. If you dont have the options either do you know how to change the Sync to vBlank and Refresh Rate settings?

Matt
In the past it was in the gconf-editor settings (see screenshot), but I am not sure about 11.04, which seems to have lost at east some of the gconf options.  Worth a look!

---

### Post by stinkeye on 2011-09-14
> **ms801000 said:**
> Thanks for checking. If you dont have the options either do you know how to change the Sync to vBlank and Refresh Rate settings?

Matt
In Natty you can find these settings in the **opengl** and **composite** plugins in ccsm.

---

### Post by ms801000 on 2011-09-14
Thanks guys, tracked them down with your help, much appreciated!

Matt

---

