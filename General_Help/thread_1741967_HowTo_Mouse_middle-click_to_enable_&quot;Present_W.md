---
title: "HowTo: Mouse middle-click to enable &quot;Present Windows&quot;"
date: 2011-04-28
forum: General Help
---

### Post by bobbob1016 on 2011-04-28
So with KDE4.6 + 11.04, it seems to be trickier to get Compiz working.  Compiz has the ability to use the middle-click on the mouse to do "Present Windows" or Scale/Expose depending on who you talk to.  If you want to set your middle click to activate "Present Windows" or Scale/Expose, there are a few simple steps you need to do.

Open a konsole window and type the following command (without quotes):
"sudo apt-get install xbindkeys-config xbindkeys xautomation"

Enable kwin desktop effects in System Settings -> Desktop Effects
Then make sure you have Present Windows enabled under System Settings -> Desktop Effects -> Present Windows
In my case, I set it to Control+F10.

Then open xbindkeys-config.
Click "New" at the bottom, next to "Delete Selected".
My settings are as follows:

Name: Present Windows
Key:  b:2
Action: xte 'keydown Control_L' 'key F10' 'keyup Control_L'

Click "Run Action" and make sure the effect enables.  I've had to play with it a bit to get it to work, but it works fine now.

Back on the main "System Settings" page, go to Startup and Shutdown, click Add Program, then either type xbindkeys or find it from the menu, so it will be enabled each boot.  You are done.

If anyone can help me clean up these directions, or pretty them up, I'd appreciate the help.  This is my first howto.

---

