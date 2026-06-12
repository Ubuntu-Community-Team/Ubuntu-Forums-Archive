---
title: "&quot;Setting sysfs variables&quot;"
date: 2010-05-28
forum: General Help
---

### Post by schmidtbag on 2010-05-28
I use Debian with squeeze repos, but since its basically just a more simplistic version of Ubuntu and the Debian forums aren't responding to my question, I figured I could ask here.

So I was using my laptop a couple days ago (running LXDE) and it was working perfectly fine, I downloaded some stuff, I updated, checked my e-mail, and shut down.  I went to go turn it on again and as its booting, its just stuck at the line:
> Setting up sysfs variables....
and it won't do anything else.  It isn't frozen, because if i press the power button or ctrl+alt+del, it responds.

I really don't feel like reinstalling everything (and I don't see why I should have to when I didn't do anything).

Anyone know what can be done about this?



EDIT:
For some additional information, if I boot up into recovery mode, I am able to login from the command line but ONLY if I continue as root, and then login as my normal username.  If I try to boot normally, it freezes at that 1 spot.  If I try to login as my username directly from recovery mode, it fails at the same spot.  The networking doesn't seem to work anymore either.  I use wicd-gtk, I do remember it updating before the system failed.





EDIT 2:
The debian forums finally helped me after 2 days, but i actually managed to figure out the issue by myself.  There was just some update problem.

---

