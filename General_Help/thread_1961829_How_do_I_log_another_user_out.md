---
title: "How do I log another user out?"
date: 2012-04-19
forum: General Help
---

### Post by sTpny on 2012-04-19
Okay.. I know I should know this, but I don't.  I've added two accounts to my system for my niece (4) and nephew (7) while I'm staying at my sisters house. They both LOVE Ubuntu, but every now and then, a game they are playing messes up. No tbiggie, unless I'm logged on as well, because I'm not always able to recover their session, and I don't know how to log them out so that I can log them in again.  Several times, I've had to hard-boot the system, and I know this isn't the right way. (can it cause problems?) So I'm wondering, how do I logout a different user, say, from virtual terminal 1. I Ctrl-Alt-F1, login to a text-session, then what.. ? 

Thanks in advance

:)

---

### Post by for.i.am.root on 2012-04-19
[http://ubuntuforums.org/showthread.php?t=1535905](http://ubuntuforums.org/showthread.php?t=1535905)

---

### Post by mccartyj on 2012-04-19
```
sudo pkill -KILL -u user
```

Kills all processes for a particular user.

---

### Post by Habitual on 2012-04-21
***DO NOT USE THIS ON root***

---

### Post by tmaranets on 2012-04-21
The very top right has a power button. It goes to a drop down menu with options. One of these options is "Log Out..." LOL LOL

---

### Post by The Cog on 2012-04-21
I recently discovered this way to kill the X server (it returns to the login screen):
1: Press and hold the Ctrl and Alt keys, and while holding them down:
2: Press and then release SysRq (same key as Prt Scr)
3: Press and then release K

---

