---
title: "Stop windows from maximizing when dragged to the top of the screen"
date: 2011-08-14
forum: General Help
---

### Post by bntlinux on 2011-08-14
One thing that really annoys me with Ubuntu 11 is that every time I move a window and it touches the top of the screen it maximizes

I have been looking for a while now to find a way to stop this from happening but couldn't find anything

Any advise on that? any configuration I'm missing?

I'm running version 11.4 with Unity in classic mode

Thanks in advance

---

### Post by CatKiller on 2011-08-14
Install compizconfig-settings-manager.

[http://ubuntuforums.org/showthread.php?t=1743309](http://ubuntuforums.org/showthread.php?t=1743309)

---

### Post by bntlinux on 2011-08-14
Thanks, That worked!

For those reading this thread, after installing CCSM:
Launch the application (System, Prefernces, compizconfig-settings-manager)
Select "Windows Management" from the list on the left
Select "Grid" from the panel on the right
Go to the "Edges" tab
Expand "Resize Actions"
On the "Top Edge" line (2nd), select None from the action list

---

### Post by coffeecat on 2011-08-14
The thread CatKiller linked suggests disabling the Grid compiz plugin. That will certainly work but will also disable other "snapping" effects that you might find useful. I agree that the automaximise can be irritating, but I find the effect you get when you drag unmaximised windows to the left or right edges very useful. I believe it's based on aero snap in Windows 7.

If you want a more fine-grained control of these effects, open compizconfig-settings-manager > Grid > Edges tab. Drop the "Resize Actions" arrow down and fine tune the various options to your preferences.

**EDIT**: I see that you worked that out while I was typing my post. Good luck! :)

---

### Post by CatKiller on 2011-08-14
> **coffeecat said:**
> The thread CatKiller linked suggests disabling the Grid compiz plugin.

Only at the beginning. Posts 6 & 7 suggest other ways to manipulate the plugin.

---

### Post by coffeecat on 2011-08-14
> **CatKiller said:**
> Only at the beginning. Posts 6 & 7 suggest other ways to manipulate the plugin.

You're quite right! A temporary lack of coffee disabled my scroll-bar.


.... I'll get my hat. :|

---

### Post by CatKiller on 2011-08-14
:)

---

### Post by Gargoulf on 2011-09-27
Thanks!!!

---

