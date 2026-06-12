---
title: "Suspend from lid, or from menu, different"
date: 2010-10-25
forum: General Help
---

### Post by parrimin on 2010-10-25
Hey. Some time ago I accepted that my laptop can not suspend well on ubuntu. But i tried one more time in maverick and... Walla! It runs.

The problem is when I suspend closing the lid, it does the same than before, it seems to turn on, but the screen is black, and can not open a terminal also (Ctrl. Alt F1). So I have to turn off the laptop with brute force.

So, the conclusion is that the script to suspend from the menu of turn off - Restart - Suspend - Hibernate, is different than the script used when I close the lid. Is there some way to see what script is running when I suspend from menu (running), and change the script when I close the lid (not running)?

---

### Post by dcstar on 2010-10-25
> **parrimin said:**
> Hey. Some time ago I accepted that my laptop can not suspend well on ubuntu. But i tried one more time in maverick and... Walla! It runs.

The problem is when I suspend closing the lid, it does the same than before, it seems to turn on, but the screen is black, and can not open a terminal also (Ctrl. Alt F1). So I have to turn off the laptop with brute force.

So, the conclusion is that the script to suspend from the menu of turn off - Restart - Suspend - Hibernate, is different than the script used when I close the lid. Is there some way to see what script is running when I suspend from menu (running), and change the script when I close the lid (not running)?

**Exactly** what are the settings in System-Preferences-Power Management?

---

### Post by parrimin on 2010-10-25
In battery mode, I put suspend on close lid. I dont know if I explained well. If I suspend from the log off menu, where you can choose to log off, or reboot, or shutdown, then, suspend runs ok. And wake up ok.

The problem is when I close the lid on battery. It seems that suspends ok, but doesnt wake up, or the screen is black and can not type the password, nor go to a terminal, nor reload X with Ctrl-Alt-Backspace

---

### Post by dcstar on 2010-10-25
> **parrimin said:**
> In battery mode, I put suspend on close lid. I dont know if I explained well. If I suspend from the log off menu, where you can choose to log off, or reboot, or shutdown, then, suspend runs ok. And wake up ok.

The problem is when I close the lid on battery. It seems that suspends ok, but doesnt wake up, or the screen is black and can not type the password, nor go to a terminal, nor reload X with Ctrl-Alt-Backspace

Is there some sort of BIOS setting that may override Linux when the lid is shut?

---

### Post by parrimin on 2010-10-25
I can not assure, but I think not. Because if there is a bios setting like that, when suspending the running mode (shutdown menu), would override too, because after suspend button click, I close the lid and go home.

You could say, so, why not just click on suspend menu? I would say, yeah, that is what im doing right now, but dude, I want this to get working! And I need to suspend, because i use the laptop to take notes on class, but the battery only let me 2 hours...

---

### Post by parrimin on 2010-10-25
No more ideas?

---

### Post by parrimin on 2010-11-03
I have no improvements on it. Anybody knows a clue to continue investigating? Im getting nervous with this and the fans going to max speed after resuming. It bothers me that sometimes in Ubuntu / Linux I am not able to make it run as Windows on simple things...

Dont misinterpretate, im using Ubuntu with happy, but i only want to solve this! I can use the system normally, but there is always some detail i cant get

---

### Post by Quackers on 2010-11-03
Is there a bios update available for your model?

---

### Post by parrimin on 2010-11-03
Ill look for that...

---

