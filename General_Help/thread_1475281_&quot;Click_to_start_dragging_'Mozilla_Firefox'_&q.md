---
title: "&quot;Click to start dragging 'Mozilla Firefox' &quot;"
date: 2010-05-06
forum: General Help
---

### Post by Sporkman on 2010-05-06
In Ubuntu 10.04, I have a desktop switcher in my gnome panel. Whenever I switch workspaces, a helpful pop-up such as the one in the thread title appears over the desktop switcher, and won't go away until I move my mouse back over the desktop switcher area.

Any way to get rid of these pop-ups? I can understand them appearing if I hover the mouse over it for a while, but that's not what I'm doing...

---

### Post by pashdown on 2010-05-07
Amen to this one.  Karmic did a similar annoyance.

---

### Post by warfacegod on 2010-05-07
Its been doing this at least since 7.04 and the only fix for this that I have come up with is to disable Tooltips (I *think* there called that anyway, its been some time) and I can't for the life of me remember how to do that.

---

### Post by Sporkman on 2010-05-13
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/356702](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/356702)

---

### Post by Sporkman on 2010-05-13
This fixes it (you just need to change the version numbers accordingly):

[http://blog.jlogday.com/2009/08/jaunty-tooltip-annoyance/](http://blog.jlogday.com/2009/08/jaunty-tooltip-annoyance/)

---

### Post by bogustrumper on 2010-06-14
Thanks, Sporkman.  That was really helpful.  

I'll point out that there's a slightly easier fix for this, too, using a PPA for ease: 

[https://launchpad.net/~renbag/+archive/ppa](https://launchpad.net/~renbag/+archive/ppa) 

I'll credit Sporkman with this find, as it's listed toward the end of the bug report that he pointed to.  But I always find using apt repos to be a lot easier than patching individual packages.

---

### Post by harto on 2010-06-18
> **bogustrumper said:**
> Thanks, Sporkman.  That was really helpful.  

I'll point out that there's a slightly easier fix for this, too, using a PPA for ease: 

[https://launchpad.net/~renbag/+archive/ppa]("https://launchpad.net/%7Erenbag/+archive/ppa") 


What package(s) should I install from that PPA?

---

