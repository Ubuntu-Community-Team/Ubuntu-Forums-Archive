---
title: "Magic key combo?"
date: 2012-03-18
forum: General Help
---

### Post by niranjan_rao on 2012-03-18
I use ubuntu 11.10 at work and at home. At work, it's dekstop, at home its laptop. Unfortunately my fingers are more used to keyboard at work than at home.

For last 4-5 days I have consistently managed to hit some magic key combo at home, that causes unity to crash. Could never reproduce it at work, or at home when I am watching my keystrokes at home.

Most of the times its happening when I try to switch to different window using alt-tab and my fingers automagically hit the wrong keystrokes as keyboard is slightly different. Theory is either some combo of windows key, function key, caps and tab key is causing unity to crash.

When I say crash, its completely gone, I dont get top menus, max/min buttons, can not switch to other applications etc. Only way out seems to be move to other terminal using ctrl-alt f2 etc and restart unity or reboot machine.

I tried checking logs, but nothing obvious. Does anyone has any ideas what's causing unity to crash. Again it seems to be happening on some key combo, but not easily reproducible.

---

### Post by jeffjardine on 2012-03-26
It is probably this bug:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/916879](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/916879)

The workaround mentioned in comment #18 - reverting to the static application switcher - solved the problem for me.

---

### Post by stanbx on 2012-04-03
I was having what I think is the same problem in Unity.  What I experienced was a crash that sometimes occurred if I pressed alt-tab while in the terminal.  I would be shown the desktop instantly and things went buggy.  I could still use some open applications, but couldn't access the top bar on anything.  Eventually I would have to restart.

And then sometimes it would flash me to the desktop and then go right on working like normal after I hit alt-tab again.

Don't know if this is correct, but it seemed to only happen somewhat recently after starting up...

Anyway, it is SUPER annoying.  I appreciate the suggestion in the previous post and I am giving that a shot.

Thanks!

S

---

### Post by rockyit86 on 2012-05-02
even i have the same problem, it is the only problem which i am facing in ubuntu 11.10, tried even 12.04, its far from stable it will take ages to make 12.04 usable.:lolflag:

can any one solve this problem ?

---

