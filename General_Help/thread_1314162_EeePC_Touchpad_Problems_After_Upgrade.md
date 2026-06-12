---
title: "EeePC Touchpad Problems After Upgrade"
date: 2009-11-04
forum: General Help
---

### Post by dannycorker on 2009-11-04
OK here's the deal - I had Jaunty on my EeePC1000HE and it worked fine - I then did a fresh install of Karmic and now I'm having problems with my touchpad. The only thing I have been unable to fix has been the functionality of 2/3 finger tapping. In Jaunty, 2 finger tap was a middle click, and 3 finger was a right click, but this has been reversed with Karmic. There's nothing in mouse settings about this and I'm totally at a loss, hence why I'm posting here. I've only been using Linux for about a month so it may be something I've completely overlooked, but if it is, just tell me that please :)

Thanks in advance.

---

### Post by Giblet5 on 2009-11-04
You might want to install gpointing-device-settings from Synaptic.

That's a GUI tool to configure Synaptic's touchpads. It also configures trackpoints, and mice. It may give you more control.

---

### Post by oldefoxx on 2009-11-05
I got a new Toshiba 17" notebook, and had touchpad issues under Vista.  My research online led me to turn off mouse tapping, which meant I had to use the two buttons, and the hover=click(s) action went away.  Thrn I found the same problem again when I installed 9.10 in dual boot mode.  My reads here indicate that there is a change in touchpad design and action, that some "modern" touchpads do not have keys with them for the mouse buttons.  The idea is that with these, you either hover over an icon to simulate the tap or click action(s), or you actually tap on the touchpad where some sensors detect the added pressure.  So operating systems adapt to something new.

What bothers some is that even if you have the buttons, the default setting is to assume that the hover or touchpad taps are going to be used.  Why not default to expecting the buttons instead?  Simple answer is that if no buttons are present, and you are not configured for the hover/tap method, you have no way to tell the PC when you want to select something.  Your mouse is effectively disabled.   So the default has to assume no buttons until you can get to the mouse settings to disable tapping (Vista) or modify the touchpad settings (Ubuntu).  That's all.

---

