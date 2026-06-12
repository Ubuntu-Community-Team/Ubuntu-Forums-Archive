---
title: "LightDM login records"
date: 2012-03-19
forum: General Help
---

### Post by az_s_za on 2012-03-19
I use the default Unity desktop and LightDM with Ubuntu 11.10.

LightDM does not seem to keep a log of graphical logins.  The commands, "last:, "w", and "who" return nothing unless there is a terminal login used.  If I change to GDM, then all these commends return expected results.

How can I keep track of users' logins when using lightDM?

---

### Post by Toz on 2012-03-19
I reported this bug a while back ([https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297")) and still waiting for a fix.

Feel free to add your name to the list of affected people.

---

### Post by az_s_za on 2012-03-20
Thanks.  I've done that.
Surpising that only 29 people have done the same.  I know for example that many mythtv users are affected by this as they have their mythtv servers check for logged users before shutting down.

My workaround has been to use gdm instead, and apply another workaround to a problem I was having with gdm.
I won't mark this "solved" though until the bug is fixed or someone can advise of another way to keep track of lightdm logins.

Interestingly, kdm also neglects to register graphical logins, so I'm sticking with gdm for now.

---

