---
title: "screen brightness changing dynamically"
date: 2010-02-02
forum: General Help
---

### Post by d3fiant on 2010-02-02
First things first, I'm new to Linux but I am a quick study ;)
 
I have just bought an Acer Revo R3610 which is an Nvidia ion netbook with the dual core atom.  It will be a HTPC connected to a large LCD TV over HDMI running XBMC.  I opted for karmic x86 and it has been an interesting but rewarding introduction to the world of Linux.  For the most part everything is working well, I am using the nvidia 185 drivers currently.
 
The big issue I have is that the screen brightness is changing dynamically, it basically dims over the course of several seconds, using the mouse can restore full brightness but it soon dims again.  I am thinking this may be a power management issue but I am not well versed on how all of this is plumbed together.  Can anyone think of any settings I can change to try to resolve this issue
 
Thanks in advance for any advice and guidance, dare I say I am a seasoned windows user who has only just started to discover the linux revolution :)
 
d3fiant

---

### Post by s.fox on 2010-02-02
Hello,

Welcome to the forum! :D

I think you are right,  sounds like a power management issue.  The power management options can be found here:
[B]
System->Preferences ->Power Management

[/B]I would check the sleep settings out.


It could also be the screen saver causing this problem.  By default the screen saver would be set to a blank screen. The settings can be found here:

**System -> Preferences -> Screensaver**

I would see how long the computer can remain idle until it activates the screen saver.

Hope these suggestions help you.

-Silver Fox

---

### Post by d3fiant on 2010-02-02
thanks for the welcome and the quick response.  I will check those when I get home from work but this problem actually occurs when Im using the PC, for example I could be using a browser and the screen starts playing up the minute I load something, it doesnt appear to wait for a period before happening.  I have confirmed its not a TV feature by testing another PC connected to the same HDMI port.  Hopefully this is just a learning curve thing ;)

---

### Post by megamania on 2010-02-02
> **d3fiant said:**
> thanks for the welcome and the quick response.  I will check those when I get home from work but this problem actually occurs when Im using the PC, for example I could be using a browser and the screen starts playing up the minute I load something, it doesnt appear to wait for a period before happening.  I have confirmed its not a TV feature by testing another PC connected to the same HDMI port.  Hopefully this is just a learning curve thing ;)
I have the same problem with an Acer 6930g. I'm pretty sure it's a bug - it started when I touched the power management config, then I managed to get rid of it by reverting the configuration, and now that I've touched it again it is back.

The screen brightness decreases after a few seconds (5/10 seconds!) of inactivity. In some cases, it goes back to normal when I touch the mouse or the keyboard, other times I have to reset it by hand.

The settings are to blank the screen after 5 minutes of inactivity, with no screensaver set.

---

