---
title: "how do i find out what cuases my lockups"
date: 2009-08-26
forum: General Help
---

### Post by ELD on 2009-08-26
Basically Jaunty seems to lock up on me at random times, sometimes right from boot, sometimes viewing websites and sometimes playing games. I cannot move the mouse or do anything, if music was playing it would do that annoying repeat.

There seems to be no one thing that does it, and i have seen many others have the problem too :(

I highly doubt it would be hardware malfunction as winxp works fine. And it didn't do it with previous versions of ubuntu.

My hardware is in my signature. Just wondering if someone can help me figure it out, it is getting annoying having to stay on windows for now.

---

### Post by danwood76 on 2009-08-26
It could be your graphics card. (I know you didnt want me to say hardware)
What drivers do you have installed?

You could try installing fglrx (the proprietary ATI driver) or if you are using that already try the radeon/radeon-hd driver.
The newest ATI cards always seem to cause issues in Linux as ATI are fairly rubbish at writing drivers. The open source drivers however are getting better everyday and are excellent for the older ATI cards.

---

### Post by danwood76 on 2009-08-26
Oh and the way to find the errors is to look in log files located /var/log.
The logs with a .0.log are usually from the previous boot but hardware issues sometimes dont show themselves from within these logs.

It could still be a hardware issue even though XP works fine as the drivers are complettely different but start with the graphics card^^

---

