---
title: "Login screen freezes when the number 2 is pressed"
date: 2012-06-21
forum: General Help
---

### Post by MegaTherion on 2012-06-21
I've been having this problem for a while, and I have to say its relatively intermittent.  My password contains the number 2 in it, and when I am entering in my password, once it reaches that character, the screen will freeze and I have to hard power down the system.

I can avoid this by using the number 2 on my numeric keypad.

Some things that I have noticed.  This issue didn't occur until I had installed the fglrx drivers that come with Ubuntu.  Also, sometimes there is a touch of graphics distortion on the screen, though you have to be looking closely to notice it, and its generally along the top 1/2" of the screen.

Running version 12.04, current fglrx drivers.  System has received updates on a daily basis as needed.  This install was done from 12.04 after release, not upgraded.

Any thoughts or suggestions on this would be greatly appreciated!

---

### Post by MegaTherion on 2012-06-23
One other thing that I have noticed, when I first boot up the laptop, if I log in quickly, and use the numeric keypad to enter in the number 2, and log in, sometimes it will flash back to the default background then bring up my custom background and require that I log back in again.

I've done a lot of digging around, and it seems that there were similar issues of sorts reported in the ubuntu bug tracker, but many have reported it as being fixed with updates to the unity-greeter, lightdm, and other packages that are related to this portion of the OS.  

I don't want to draw any conclusions as their issues seem to have been addressed, but I venture a guess that the fglrx driver somehow is not communicating properly with X at this portion of the boot?

Very stumped.

---

