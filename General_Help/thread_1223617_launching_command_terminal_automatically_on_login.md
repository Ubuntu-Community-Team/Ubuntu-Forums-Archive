---
title: "launching command terminal automatically on login?"
date: 2009-07-26
forum: General Help
---

### Post by bjdonhauser on 2009-07-26
Q: How do I get the command terminal to launch automatically on login?

I'm only interested in doing this locally (i.e., only for my particular user account) so the "System -> Startup Applications" isn't what I want to do...right? 

I tried adding "gnome-terminal" to the end of my ~/.profile. Didn't work. What's wrong? shouldn't that be enough to launch the bash terminal? (I'm not sure if I'm saying things correctly here...I'm a complete noob. Thanks for bearing with me)

P.S. running ubuntu 9.04

---

### Post by Whiffle on 2009-07-26
System > Preferences > Startup Applications is what you want.

---

### Post by bjdonhauser on 2009-07-26
> **Whiffle said:**
> System > Preferences > Startup Applications is what you want.

OK, good to know. Thank you. 

Still, I'd like to know why "gnome-terminal" at the end of my ~/.profile won't run it.

---

### Post by Whiffle on 2009-07-26
I'm pretty sure .profile is what used to get run whenever a terminal is opened, for setting the $PATH variable and such, I don't think gnome reads it on login.

---

### Post by bjdonhauser on 2009-07-27
> **Whiffle said:**
> I'm pretty sure .profile is what used to get run whenever a terminal is opened, for setting the $PATH variable and such, I don't think gnome reads it on login.

Wait, it's read on login isn't it? At login a login shell has to be run to interpret/execute a number of commands. I was asking about this in another thread as well. Maybe gnome-terminal actually runs but is then closed out once ~/.profile is done being run?

---

