---
title: "New to Ubuntu"
date: 2009-08-16
forum: General Help
---

### Post by wood man on 2009-08-16
Hey everybody. Just got Ubuntu 9.04 yesterday after a Windows melt down. I am NOT good at computers, period. Still, the guy that put this on my old computer thought it might kind of get me ready for a Mac, etc. My old computer helper (my son) is in his last year of college and doesn't live at home so I'm on my own. Three questions: 1. If I walk away from my  computer for a few minutes and the screen saver comes on, when I come back and move my mouse, the shape of the screen changes to the "pincushion" but only on the right side. I have gone into the monitor controls on the monitor and chosen factory resets which will fix it but then the same thing happened later after taking a break. Any ideas? 2. Tried to get on You Tube but was told I needed the latest Adobe Flash Player. Tried to download one but am not sure if it was the correct version for Ubuntu.  Was going through the steps OK until box comes up asking for administrator password. Clueless. 3 Why does number pad off to the right of my keyboard not work unless I hold down the Shift key (found that out by accident!) Folks, remember I am really challenged. As a matter of fact, as soon as I send this I may go for a Miller High Life. Any help would be greatly appreciated! Wood

---

### Post by michy99 on 2009-08-16
This should fix your flash problem. Open a terminal (Applications -> Accessories -> Terminal) and enter this command:```
sudo apt-get install flashplugin-nonfree
```It will ask for password. Use your log-in password. When you type it, you won't see anything on the screen, just type it and press Enter. If you get a screen asking you to accept a user agreement, uses the Tab key to select OK and press Enter.

---

### Post by 4Orbs on 2009-08-16
Some of the screensavers demand more resources than are available on older computers. You might go to the screensaver settings and choose one that is 2D rather than 3D, or select the option to only blank the screen.

If your son set the computer up with you as admin, then your normal user password is also the admin password.

To fix the flash player, I suggest going to the Multimedia and Video section of this forum and follow the instructions on the sticky thread "Comprehensive Multimedia and Video How-To". That should take care of your audio/video playback and flash.

---

### Post by wood man on 2009-08-16
Thanks guys!

---

### Post by geirha on 2009-08-16
3. The numpad doubles as arrow keys, page up/down, home and end (Never had a use for those myself as they're already available in the section left of the numpad, but I guess it's just something left over from the olden days). 

There should be a button labeled "Num lock" at the top left of the numpad, and tapping it should toggle whether the numpad keys produce numbers or arrows etc.. On most keyboards there will be a led indicating whether it is on or off as well.

Oh, and I recommend you read through the documentation at [http://help.ubuntu.com/9.04/](http://help.ubuntu.com/9.04/). It covers the basics of using Ubuntu 9.04.

---

