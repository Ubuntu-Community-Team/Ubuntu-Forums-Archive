---
title: "I have TWO gnome-screensaver processes!"
date: 2010-07-08
forum: General Help
---

### Post by peterx14 on 2010-07-08
Hi all,

I've recently installed Ubuntu 10.04 on a MacBook 3,1 and I had noticed the screen saver was not working; the screen would go blank, but the screensaver would not appear.

Using PS I see that there are 2 "gnome-screensaver" processes running, one owned by me and the other (with a lower PID) owned by gdm.

I can kill both of these and then start a new gnome-screensaver daemon, and then it works.

This is a fairly clean install (at the moment) so I'm not sure what would've caused this issue. I did install the "rss-glx" package for additional screensavers, so I did a complete removal of that in case that caused the problem, but it didn't help.

AFAIK the gnome-screensaver process should be owned by me, so any idea what's starting the gdm owned one?

Thanks in advance!

Peter.

---

### Post by lemoirl on 2010-07-26
Bump!

I have the same problem... It's a real pain since I use password locking so I have to enter my password twice now to get out of the screensaver.

---

