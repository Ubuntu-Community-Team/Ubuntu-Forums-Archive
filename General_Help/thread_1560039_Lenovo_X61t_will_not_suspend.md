---
title: "Lenovo X61t will not suspend"
date: 2010-08-24
forum: General Help
---

### Post by jbiggs12 on 2010-08-24
Hello World,

I'm having a bit of trouble with my Lenovo thinkpad. Usually, on a fresh install, when I tell my computer to suspend (either by Fn-F4 or selecting it from the menu) it suspends itself. From time to time, however, the computer will lose the ability to suspend and will simply darken its screen and flash the little moon crescent indefinitely, upon which I have to hold down the power button to shut it off.

Does anyone have a fix for this?

---

### Post by hjm on 2010-09-21
Same problem with a Thinkpad T60 with 10.04 KDE.  When it works (about half the time), it works well.  When it doesn't, it does what the 1st poster says.  

The Thinkpad keys don't work anymore either (Fn+F4 to suspend) as they did with Hardy (which worked so solidly that I left it only because some software I needed wouldn't work anymore..)


hjm

---

### Post by Full_Auto_Legos on 2010-09-21
I am using a Lenovo W500 with similar problems.  I have never gotten the suspend/hibernate/screensaver settings to work unless I go to terminal and hardpunch the "xset" settings:
To Take a look at your xset settings:
$> xset -q
Change the screensaver timeout to zero
$> xset s 0
Change the DPMS Standby, Suspend, OFF settings 
$> xset dpms 3600 0 0
(Standby 3600 seconds, Suspend to 0 which is off, OFF to 0 which is off/ignored.)

I know that doesn't really answer your question directly, but maybe editing your xset is what you are looking for.

---

