---
title: "Dude, Where's My Battery?"
date: 2012-02-08
forum: General Help
---

### Post by JDog2pt0 on 2012-02-08
Witty title eh? Long story short, formatted, reinstalled, battery life went to crap.

Long story: Before I formatted I had Ubuntu 11.10, from an 11.04 upgrade. I had Unity, Gnome 3, and Cinnamon. Battery life was fantastic, lasted hours and hours. Things got a little fudged and my whole computer was messy so I just decided to do a fresh start. I installed Ubuntu 11.10 and Cinnamon (all I use) and my battery life took a turn for the worse. Now, your probably thinking "Well your battery is bad", and those thoughts have passed through my head too. Problem is the battery is less than a year old, and I just find it coincidental that after a fresh install, battery life drops.

Let me know what you think

---

### Post by JC Cheloven on 2012-02-08
Probably you're hit by a known [kernel issue]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131") that drains the battery life. It affects versions later than 2.6.38 (Natty onwards). There is currently a patch, which will be included in Precise 12.04, and in linux kernel 3.3. But for Ub11.10 it seems regular updates will not fix that.

According to comment #242 there, for oeniric 11.10 we can install the upstream 3.0.20 kernel from [this ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). I'm just about to try myself.

Only, I wonder why you didn't observe the same battery drain in your previous 11.04 and 11.10 installs.

---

### Post by JDog2pt0 on 2012-02-08
Thanks for the reply. My previous install was "messy". I had a lot of odd packages, repos tweaks, etc. I agree that it's odd that I wasn't affected before, but I would imagine it had something to do with all that. I think I'm going to go ahead and install the kernel as well. This thing used to have awesome battery life. Low power laptop and an extended battery.

---

### Post by JDog2pt0 on 2012-02-13
I found this as well

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

---

### Post by JC Cheloven on 2012-02-13
> **JDog2pt0 said:**
> I found this as well
[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)
You don't loose anything by trying, as all that is reversible. 

As for the kernel issue, I had time to test the one I mentioned. It seems to work fine (at last!). Please see post #6 [here]("ubuntuforums.org/showthread.php?p=11686854").

---

