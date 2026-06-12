---
title: "Suspend/Hibernate on Toshiba Satellite L305"
date: 2009-09-03
forum: General Help
---

### Post by abelian jeff on 2009-09-03
I am having two problems involving the suspend/hibernate power saving options with my Toshiba Satellite L305 running Jaunty 9.04.

First, using gnome-power-management, if I set my latop to hibernate or suspend when I close the lid, it does not work. It seems as if the laptop is not recognizing that the lid is closed.

Second, if I choose to suspend/hibernate from the Shut Down menu on the panel, I get a black screen (with white cursors flashing in the corners occasionally). Furthermore, pressing buttons does not wake the computer back up.

Any help will be greatly appreciated!!

---

### Post by steve161 on 2009-09-03
I have a toshiba satellite l305 and I have tried almost everything to no avail.  One positive thing to report is that I have upgraded my kernel and drivers (for other reasons) and now my laptop does go into hibernate, but takes as long as a normal reboot to return.  It also does go into suspend but will not wake up, whereas the default jaunty setup would not even go into suspend.  So I am thinking that karmic may solve our problems.

---

### Post by steve161 on 2009-09-14
Update:   I have installed the latest stable kernel (2.6.31) and the latest drivers from
xorg-edgers PPA, and both suspend and hibernate work perfectly.

---

### Post by rygar on 2009-09-23
> **steve161 said:**
> Update:   I have installed the latest stable kernel (2.6.31) and the latest drivers from
xorg-edgers PPA, and both suspend and hibernate work perfectly.


i am having the same problem...

how do i upgrade to the latest kernel, and what is xorg-edgers PPA?

thanks,
jeff

---

### Post by rscow on 2009-11-09
I have a toshiba L305 as well.  Using the Karmic beta, I was able to suspend and hibernate, which I had never been able to do in Jaunty.  When I finished the upgrade from the beta to the full Karmic late last month, I couldn't suspend.  I would get a dim screen, but the backlight stayed on, and it would "wake right up."  I was a little disappointed.

This thread lead me to the xorg-edgers ppa.  I, too, had no idea what it was.  A google search lead me to [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) and I installed the xorg-edgers sources in my /etc/apt/sources.list.  Then apt-get update and apt-get upgrade.  It installed a bunch of stuff.

Now my hibernate and suspend both work.  

Thanks for the tip, steve161.  You might want to try it, rygar

Roger

---

