---
title: "keyboard layout persistant usb install"
date: 2012-05-29
forum: General Help
---

### Post by DMarkac on 2012-05-29
I have got the same problem with updating 12.04 on a 40 GB flash drive with persistant file, but beside this I lost my keyboard layout settings (for croatian language) and cannot add it again or restore it anymore. I tried through menu system settings>keyboard layout>(+) sign for adding - no results. This makes my ubuntu unusable for me. 

 Also, up to now I have spoted a few trivial problems like desktop background picture and side-menu listings set to default but this is not so important now.  

My 3 questions are:
1. Is there any method to make ubuntu updates normally?
2. can I restore my ubuntu 12.04 to state before updates?
3. how can I add keyboard layout?

---

### Post by nothingspecial on 2012-05-29
Question moved to it's own thread.

---

### Post by wilee-nilee on 2012-05-29
> **DMarkac said:**
> I have got the same problem with updating 12.04 on a 40 GB flash drive with persistant file, but beside this I lost my keyboard layout settings (for croatian language) and cannot add it again or restore it anymore. I tried through menu system settings>keyboard layout>(+) sign for adding - no results. This makes my ubuntu unusable for me. 

 Also, up to now I have spoted a few trivial problems like desktop background picture and side-menu listings set to default but this is not so important now.  

My 3 questions are:
1. Is there any method to make ubuntu updates normally?
2. can I restore my ubuntu 12.04 to state before updates?
3. how can I add keyboard layout?


With that size of a usb I would do a full install on it, it will run better and be more stable.

A ISO loaded usb with a persistent file is not really setup for updates, you're basically still running off the ISO.

Not sure about the keyboard.

---

### Post by DMarkac on 2012-05-30
I backed up my data from this 40 GB disc and installed fresh new ubuntu with boot loader ON IT (not changing windows boot loader on my system). I've never before thought about possibility to install boot loader on any other disc then C: (sda/). 

Now it runs PERFECT! Just a few secs on start to set a boot priority in BIOS and I'm ready for work. No more keyboard layout issues, updates are applied quietly, system is faster then before.

Thank you very much for this help.

---

### Post by wilee-nilee on 2012-05-30
> **DMarkac said:**
> I backed up my data from this 40 GB disc and installed fresh new ubuntu with boot loader ON IT (not changing windows boot loader on my system). I've never before thought about possibility to install boot loader on any other disc then C: (sda/). 

Now it runs PERFECT! Just a few secs on start to set a boot priority in BIOS and I'm ready for work. No more keyboard layout issues, updates are applied quietly, system is faster then before.

Thank you very much for this help.

Cool, I was wondering if the keyboard problem was a anomaly.

You can use a boot from menu outside the bios as well, rather then changing the bios, mine is a f12 prompt, like you would to access the bios. The bios splash should say what that key or keys are.

---

### Post by DMarkac on 2012-05-30
my splash screen says nothing about boot options. I tried to search inside BIOS and found f8 function key which initiates boot menu. Now I'm few secs faster in booting. Yeah!
:guitar:

---

