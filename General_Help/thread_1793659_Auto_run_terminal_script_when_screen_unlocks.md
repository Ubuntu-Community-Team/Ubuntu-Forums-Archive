---
title: "Auto run terminal script when screen unlocks"
date: 2011-06-29
forum: General Help
---

### Post by KiloKai on 2011-06-29
So I am still pretty new to linux, but I am getting to know things more and more every day thanks to this forum and others. But today, I have a problem that I haven't found an answer too.

I have an Asus Eee netbook that has two finger scroll functionality. I installed ubuntu and found a way to get the two finger scroll functionality to work through a terminal script. I have it set up so that the script runs on start up and everything is fine in the world. Until the screen locks and I have to unlock it (enter in my password). At that point, the scrolling functionality no longer works and I have to rerun the script in order to enable the two finger scrolling again.

So, my question is: is there a way to have the script run when the screen unlocks or am I not it right in the first place. The script has only the following that I made executable:

> synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48Any help would be appreciated.

---

### Post by qritiq on 2011-07-20
bump

---

### Post by Toz on 2011-07-20
Does this help? [http://blog.troyastle.com/2011/06/run-scripts-when-gnome-screensaver.html]("http://blog.troyastle.com/2011/06/run-scripts-when-gnome-screensaver.html")

---

### Post by twistedrabbit on 2011-11-28
Hate to revive this, but what do i do once i set up what was on that link? Do i add the script to the ssStart file? or the location?

---

### Post by Toz on 2011-11-28
Based on the information in that link, I would add your script information to the /opt/ssTrigger/ssStart and /opt/ssTrigger/ssStop scripts.

---

