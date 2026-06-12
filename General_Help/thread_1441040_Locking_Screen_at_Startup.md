---
title: "Locking Screen at Startup"
date: 2010-03-28
forum: General Help
---

### Post by plapczynski on 2010-03-28
Hi,   

I looked for this but couldn't find it.

When Gnome starts, I would like to auto-login a user account, but I and the screensaver to lock at boot.  I am using the gnome-screensaver.

Any ideas?

---

### Post by labinnsw on 2010-04-04
> **plapczynski said:**
> Hi,   

I looked for this but couldn't find it.

When Gnome starts, I would like to auto-login a user account,

Go to: System >> Administration >> Login Window. Under the Security tab, check Enable Automatic Login for the desired user.

> **plapczynski said:**
> 
but I and the screensaver to lock at boot. I can't honestly say that I understand this phrase, but if you want to make adjustments to how the screensaver behaves, go to: System >> Preferences >> Screensaver.

---

### Post by cjhabs on 2010-04-04
> **plapczynski said:**
> Hi,   

I looked for this but couldn't find it.

When Gnome starts, I would like to auto-login a user account, but I and the screensaver to lock at boot.  I am using the gnome-screensaver.

Any ideas?

I haven't tried this, but how about putting the screen saver into:
system -> preferences -> startup applications

---

### Post by labinnsw on 2010-04-04
> **cjhabs said:**
> I haven't tried this, but how about putting the screen saver into:
system -> preferences -> startup applications

To do this, the code is ```
gnome-screensaver-command --activate
```

---

