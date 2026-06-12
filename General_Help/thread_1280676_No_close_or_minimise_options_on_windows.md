---
title: "No close or minimise options on windows???"
date: 2009-10-02
forum: General Help
---

### Post by rock it on 2009-10-02
Hi,
Can anyone help with this?
I just saved nVidia server settings with root privilages.
As suggested here [http://ubuntuforums.org/showthread.php?t=471256](http://ubuntuforums.org/showthread.php?t=471256)
Then I restarted the computer and everything seemed fine until I go to close the window and theres no minimize maximize or close options?

meanwhile I can right click the panel to close, its just quite annoying :P

thankyou all.

---

### Post by NightwishFan on 2009-10-02
Can you give me an example of what you mean? Is there no titlebar or are the buttons just absent? Also you should not save Nvidia settings with root privileges it is a user permission application. You will need to run as normal user and then set the command nvidia-settings -l to run when you log in. You can do so in System -> Preferences -> Startup Applications (something like that)

You can also try setting desktop effects to none in:
System -> Preferences -> Appearance -> Desktop Effects

---

### Post by rock it on 2009-10-02
It's the whole title bar which is absent. The buttons work with the effects off :P.  Its more usable now :). Is there a way to get back my buttons with the desktop effects?

(Its actually the whole title bar)

---

### Post by rock it on 2009-10-02
bump

---

### Post by urosg3 on 2009-10-02
are you use Emerald?

---

### Post by rock it on 2009-10-02
Unsure, whats emerald? (sorry if thats a stupid question, but Im a beginner)

---

### Post by rock it on 2009-10-02
> **rock it said:**
> It's just the buttons which are absent. The buttons work with the effects off :P.  Its more usable now :). Is there a way to get back my buttons with the desktop effects?

It's actually the whole title bar which has gone. sorry about that. Hope that helps

---

### Post by urosg3 on 2009-10-02
Emerelad is window manager, try to install it from synaptic. Also compiz fusion icon. After type in terminal

> emerald --replace
and turn on effects

sorry for typo errors

---

### Post by tacantara on 2009-10-02
OP:  I feel your pain, as the same thing happened to me when I first enabled desktop effects.  Hopefully this will help:

Emerald is a "theme manager" available when you enable Compiz Fusion.  It allows you to do some interesting window dressing, including the hiding of the title bar from program windows (which appears to be the issue at hand).  If you don't have it open already, click the Compiz Fusion icon.  This will add Fusion to your system tray.  Right-click the Fusion icon in your system tray, and select Emerald Theme Manager.  From the menu, check to see which window decorator is active (GTK, KDE, or Emerald).  If Emerald is checked, then check the Emerald Theme Manager settings (right click the Fusion icon in the system tray again).  You should be able to make the necessary tweaks from there.

Or, you can just go with the advice that urosg3 posted ahead of me.  Late again, as usual :)

---

### Post by rock it on 2009-10-02
nothing I try is working. Not quite sure how to use the Emerald Theme manager.

---

### Post by sabre2th on 2009-10-02
If you just want it to work and don't care about having the fancy title bars, hit alt-f2 and type
```
metacity --replace
```

I'm a bit rusty, but I believe that should bring back your old title bars.

---

### Post by rock it on 2009-10-02
thanks, I got it working without the fancy. Will keep checking back to see if anyone finds a solution to fix it proper.

---

### Post by sabre2th on 2009-10-02
The metacity command worked, then?

If you want Emerald, it should be as simple as installing the package in Synaptic and doing what they said above.

Is there something else I'm missing?

---

### Post by rock it on 2009-10-02
I changed to metacity and that worked. Emerald did not work. However re-installing my graphics driver fixed the problem.

---

### Post by urosg3 on 2009-10-02
OK. But Emerald must work with proper graphic driver, Emerald is part of Compiz and without driver cant work, so if you want Emerald you must install proper driver.
Cheers

---

