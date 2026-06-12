---
title: "ubuntu prompts for password after hibernate, tried other suggestions"
date: 2009-07-30
forum: General Help
---

### Post by mano the shark on 2009-07-30
I have a laptop (sony vaio) with ubuntu 9.04 that properly hibernates and resumes.  Upon resuming from hibernation it prompts me for a password.  I've tried the following:

-gconf-editor and unchecked hibernate and suspend under /apps/gnome-power-manager/lock
-commented out LOCK_SCREEN=true in /etc/default/acpi-support
-screen saver is not set to lock the screen when active

I didn't see anything else on the forums and any additional ideas or suggestions would be helpful.

---

### Post by lisati on 2009-07-31
Have you entered your password?

---

### Post by mano the shark on 2009-07-31
Thanks, but I entered the password.  I'm looking to remove the password prompt as I'd rather not have to give the password to everyone that wants to use the computer.  Nothing that I care about is kept on the computer and I already have it set to auto-login.

---

### Post by Post Monkeh on 2009-08-01
i know it's not exactly what you want, but couldn't you just set up a new user with a simple password (like password) and let anyone using the computer use that account?

---

