---
title: "Top, Bottom window toolbars have both vanished"
date: 2010-09-19
forum: General Help
---

### Post by Vitruvian Bacon on 2010-09-19
I turned on my computer today and logged in only to find discover that both toolbars on the top and bottom of my screen have disappeared. 

This is problematic as it has become impossible for me to connect to the internet without the wireless toolbar at the top of the screen, and as well I no longer have the ability to select different windows without alt+tabbing. I didn't modify my system in any way to the best of my knowledge, nor was I messing around with my desktop config. Luckily I can still access my applications (including the Terminal) by right clicking, but it's still a less than ideal setup.

What could have gone wrong that would make my toolbars dissapear? And more importantly, how can I get them back? 

Sorry to bother you all, but I'm still a relative Linux newbie.

---

### Post by afrowildo on 2010-09-20
Try this command

```
rm -r ~/.gconf/apps/panel
```

Then log out and back in again. This will reset your gnome panel by deleting the current configuration and replacing it with the default when you log back in.

---

### Post by Vitruvian Bacon on 2010-09-21
According to my Terminal there is no such directory. There is a ~/.gconf/apps folder, but no panel subfolder within it.

---

### Post by afrowildo on 2010-09-24
Here's a thread started by someone who appears to have the same problem as you. They found a solution among the many suggestions in there, so hopefully you'll find something too.

[http://ubuntuforums.org/showthread.php?t=840105](http://ubuntuforums.org/showthread.php?t=840105)

---

### Post by QLee on 2010-09-24
I guess we shouldn't be too surprised that the OP doesn't have a GNOME configuration because, if I am correct, an Xbuntu install won't have GNOME as the DE. 

Unfortunately, I've never run, or even seen, an Xbuntu installation so I can't give you a definitive answer but you'll probably find some similar way to correct the problem. Some Xbuntu user will have the correct answer for you.

---

### Post by azertyh on 2010-09-24
hi,
ALT+F2 and type
```
**xfce4-panel**
```and ENTER

---

### Post by Vitruvian Bacon on 2010-09-27
> **azertyh said:**
> hi,
ALT+F2 and type
```
**xfce4-panel**
```and ENTER

That did it! My toolbars are back and everything seems back to normal! Thank you all for being so helpful. :)

---

