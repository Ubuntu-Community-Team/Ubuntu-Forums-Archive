---
title: "How do I get my window control buttons back? (close, min, max)"
date: 2012-09-11
forum: General Help
---

### Post by sienile on 2012-09-11
I had to power off my PC forcefully (hold power button) when it somehow froze during a log-off. When I rebooted my desktop was in Chinese (fixed that) and my window controls are gone. How do I get my buttons back?

---

### Post by critin on 2012-09-11
Did you see this post?  The poster has an older version, but some of the answers apply to 12.04.  Crashing Window managers.

Someone will come along and show you how to fix this through terminal, ( if your WM crashed during the hard power shut-down)  Using the Terminal makes it easier.  lol


[http://ubuntuforums.org/showthread.php?t=2038728](http://ubuntuforums.org/showthread.php?t=2038728)

and:
[http://ubuntuforums.org/showthread.php?t=2000851](http://ubuntuforums.org/showthread.php?t=2000851)

---

### Post by sienile on 2012-09-11
Thanks, but I've noticed my problems are more serious.... **I can't open ANY terminal program.**

Is there a way to do a system repair without reinstalling? I've already tried all the recovery options. Got my window controls back, but in the fallback theme and with no way to change them from that. Was going to try to fix things through terminal, but it's fubared.

---

### Post by critin on 2012-09-11
You can't even open a terminal?!  You could try going in through the guest session login, but if something on the system is broken, it wouldn't help.  Try it though.  

> 
Is there a way to do a system repair without reinstalling? Not that I know of, not without a terminal at least.  

Did you try to get to the terminal by alt+ctrl+t  ?

Installing a new desktop environment from synaptic package manager would at least give you a desktop.   Did you have to install the fallback session right now or did you have it already?

---

### Post by critin on 2012-09-11
> Got my window controls back, but in the fallback theme and with no way to change them from that.Things work now except for the terminal?  Go to synaptic, click Status,  and look at the bottom of the lists for number of packages, etc. and see if it says anything about 'broken' packages.

---

### Post by sienile on 2012-09-11
Synaptic reports 0 broken packages, but the dpkg recovery had reported that blueman had issues. Either way, none of that deal with terminals or themes.

Ctrl+Alt+T doesn't work, but I've found a way to get around the terminal problem. My preferred file manager, Krusader, has a built in terminal that works fine.

When I had mentioned fallback theme, I actually meant fallback _theme_, not the fallback session. I use Gnome Classic normally. The absence of the Ambiance theme when I select to use it for windows is what made me refer to it as the fallback. Instead of my nice circles, I have a cartoonish version of the MS Windows buttons... on the right, even though my settings are set to left.

I'll try your suggestion about logging in through the guest session and see if that makes a difference.

---

### Post by sienile on 2012-09-11
Yeah... It made a difference alright. I had no desktop at all. Only thing that popped up was Gnome-Do... and it couldn't even run logout. Had to hard off again.

I think it's pretty safe to say this install is fubared. Time to back up all my files and reinstall. Just hate there's no recovery install option so I could skip the backing up and just go for it.

If you come up with any miracle solutions between now and tomorrow night, I'll try them out. Not like it could possibly hurt anything. :P

---

### Post by critin on 2012-09-12
No, instead of  installing something that would just confuse it more, I agree with you--it's gone.  Give it a fresh install.  It doesn't take long.  Sorry I couldn't help.

---

