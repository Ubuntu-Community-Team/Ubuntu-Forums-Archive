---
title: "Random freezes, keyboard unresponsive and can't use SysRq"
date: 2009-11-16
forum: General Help
---

### Post by juanchito2006 on 2009-11-16
Since Intrepid, I'm experiencing random freezes in my system, the screen freezes and the mouse doesn't seem to respond, if audio is being played in the time of the freeze, it's stuck in a loop. The keyboard is unresponsive, pressing Caps Lock won't switch the respective LED and the Magic SysRq key won't work even, prompting me to restart the machine manually.

This issue has persisted through Karmic and is affecting my productivity heavily as these freezes occur on a daily basis. How can I diagnose the issue? What info should I submit?

---

### Post by Trevor Bramble on 2009-11-16
While I don't have any suggestions for how to *fix* your problem, you may be able to avoid it, if it's like what I described [here]("http://ubuntuforums.org/showthread.php?t=1278048").

Basically what I determined was that it's usually triggered when waking up from suspend, and that there's an open bug report on the issue.  So I've been avoiding use of suspend and haven't run into the problem again.

---

### Post by juanchito2006 on 2009-11-16
Though I've used suspend scarcely, I believe it's an unrelated issue since most if not all of the times my system freezes just after a regular start up and the system has been running for hours. I tried to read logs but they don't seem to point to anything unusual. Any info from my system I should post?

---

### Post by juanchito2006 on 2009-11-20
This issue is haunting me as of late. It's quite rare to see my machine on for over a day. Any help?

---

### Post by P4man on 2009-11-20
Did you run a memory test? From the grub menu select memtest and let it run overnight.

If your ram is fine, id try narrowing the problem down by disabling your videdrivers (which card do you have?) and revert to vesa drivers and see if that helps.

---

### Post by juanchito2006 on 2009-11-20
Will run Memtest, though the last time I checked, RAM was OK.
I'm using an Intel GMA X3500 graphics chipset, using the X.Org intel driver. I doubt using Vesa would be sane on my widescreen monitor, plus having a high chance of losing compositing.

---

### Post by P4man on 2009-11-20
Using vesa would be painful but if it solved the problem you know where to look for a solution, as it will be the intel drivers causing it. Perhaps less painfull is disabling desktop effects if you have them enabled. Go to system > preferences > appearance > visual effects. set them to none.

---

### Post by juanchito2006 on 2009-11-28
OK, freezes are still going on, so I ran Memtest twice with no errors and switched to Metacity, let's see if the issue persists. Any more info I should provide?

---

### Post by juanchito2006 on 2009-11-30
Freezes are still happening with Metacity. How do I track the issue? I'm not really sure about it.

---

### Post by gribbsy on 2009-11-30
I'm also having the random freeze problem as you have described.  My system is a Gateway E-2000 with integrated Intel graphics driver.  I had to revert to Jaunty which works fine.  

Every time I try to do a fresh install of Karmic, system runs great for a couple of hours then it freezes.  I am running Pandora (internet radio) and Pogo (Java-powered online card games)

---

### Post by Buggin on 2009-11-30
also having a freeze problem with karmic... only in gnome... within a minute of login every single time now... nvidia drivers
xfce works fine but i hate it

---

