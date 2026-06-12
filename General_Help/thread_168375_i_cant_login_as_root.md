---
title: "i cant login as root"
date: 2006-04-30
forum: General Help
---

### Post by kolobaki on 2006-04-30
hello everybody!
well,i want to login as root and when i try this it say "root logins are not allowed".
Can help me anyone?
thx alot!

---

### Post by aysiu on 2006-04-30
Sure. Read these two webpages:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by _linux_ on 2006-04-30
By default, the root password is disabled on Ubuntu. You can run sudo in the terminal when you need to run something that requires root priviliges. If you still want a traditional root account, go to the RootSudo wiki page that aysiu has in his post.

---

### Post by kolobaki on 2006-04-30
you're great.
Thanks again!

---

### Post by Ian Maxwell on 2006-04-30
If it said "root logins are not allowed" instead of just "login incorrect", then I assume you're trying to do a *graphical* login as root. This is a Bad Idea, because running a graphical session involves all sorts of system processes that you don't want to have root privileges.

This protection can be turned off in via System -> Administration -> Login Screen Setup, but as a rule there is no good reason to turn it off. (When a distro locks the root account, the assumption is that, if you know enough to enable it, you'll know enough not to.)

---

