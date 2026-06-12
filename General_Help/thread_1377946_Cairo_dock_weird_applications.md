---
title: "Cairo dock weird applications"
date: 2010-01-10
forum: General Help
---

### Post by oliverjia on 2010-01-10
Dear all,
    Today I had this weird new icon appeared on my Cairo dock (The grey rectangular box sitting in the middle). Right click on it, choose whatever action, it just won't disappear. very annoying.
    Anyone knows how to get rid of it? You help is much appreciated.

---

### Post by lidex on 2010-01-10
That's a default icon - could be anything. Do your open apps appear in that section? You could try restarting it (or your system). Look in System Monitor to see what it might be.

---

### Post by polki@mac.com on 2010-01-11
It's very annoying. Very.

I right click on the dock, close it and start it again. Works for me. But I'd love to know why the default icon pops up there in the first place...

---

### Post by fabounet on 2010-01-11
what is this application ? can you find it in the list of current tasks ?
please post here the debug output (cairo-dock -l debug), there might be some clue.
also, did you do sime update of your system recently ? you seem to say it never occured before.

Edit : which version of the dock are you running ?
you might want to try with the 2.1.3 in case it fixes the problem (it is available on the PPA, on Launchpad).

---

### Post by lidex on 2010-01-11
Launchpad PPA for stable is here:
[https://launchpad.net/~cairo-dock-team/+archive/ppa]("https://launchpad.net/~cairo-dock-team/+archive/ppa")

It's at 2.1.2 -- 2.1.3 must be in unstable.

---

### Post by oliverjia on 2010-01-11
Thanks all for responding to my post.I guess that grey icon started to appear after I upgraded the linux kernel to 2.61.3.17, together with many other updates. I am not sure which application the grey icon is corresponding to, since when I hover my mouse over it, it gives no information at all. Please see my attached img for the running processes. 
BTW, closing cairo dock then open it seems solved the problem. But once restart ubuntu, the grey icon appeared again..
Thanks again to all!
regards, 
oliver

---

### Post by lidex on 2010-01-11
Yeah, I had that until I updated to 2.1.2. Now my only issue is dock restarts when quitting so I have to kill it in system monitor.

---

### Post by fabounet on 2010-01-11
2.1.3 is the weekly package
since our site is down for now, we can't release it, but it's quite stable ^_^

---

### Post by wiebeest on 2010-01-11
> **fabounet said:**
> 2.1.3 is the weekly package
since our site is down for now, we can't release it, but it's quite stable ^_^

Any idea when the website will be up again? Everytime I run the update manager it nags about not being able to find  the 'repository.cairo-dock.org'.

Using version 2.1.2-4 and happy to say it runs quite stable already. 

Loved how you guys simplefied the configuration settings over time. 
My sincere compliments on this great dock!

---

### Post by lidex on 2010-01-11
> **wiebeest said:**
> Any idea when the website will be up again? Everytime I run the update manager it nags about not being able to find  the 'repository.cairo-dock.org'.


You can wait for it if it is coming back but there is a Launchpad PPA for it here:
[https://launchpad.net/~cairo-dock-team/+archive/ppa]("https://launchpad.net/~cairo-dock-team/+archive/ppa")

---

