---
title: "karmic doesn't like gnome-do"
date: 2009-11-01
forum: General Help
---

### Post by Afkpuz on 2009-11-01
I know there is a bug filled and I'm tracking it, but I wondered if anyone knew of a workaround.  

So, running ubuntu 9.10 and everything is great, except gone-do.  Sometimes, it will open, but most of the time, nothing happens when I ask it to open.  There is no feedback when run from terminal either.  I've tried opening it automatically at startup, and after the system has booted.  Any ideas other than track the bug?

---

### Post by Afkpuz on 2009-11-02
Well, I discovered that you can do

```
sudo killall gnome-do
```

Then reopen it.

Seems to work, but not sure for how long.

---

### Post by JebusWankel on 2009-11-03
What bug? I'm affected, but I can't find it in Launchpad/

---

