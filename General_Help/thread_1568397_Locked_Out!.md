---
title: "Locked Out!"
date: 2010-09-05
forum: General Help
---

### Post by pokepal101 on 2010-09-05
Hi. I recently made the switch from Windows XP to XUbuntu on my laptop. XUbuntu was the only choice I had because of low RAM issues.
Also, I disabled gdm with both renaming /etc/init/gdm.conf and modifying /etc/default/grub to boot with "text" parameter.

When I login to tty1, everything works fine. I run "startx" and I do some stuff. When I close my laptop lid, the system goes into "lock screen". When I open it again, I can login again with my password.

However, a few times later, I cannot log in again and I get an "Authentication failed!" message. I've checked my caps-lock and stuff, and I've tried a million times, but I can't get the system to log-in again. I have tried to login on tty2 and it works fine.

Can someone help me???

---

### Post by Jose Catre-Vandis on 2010-09-05
Just to be clear, is this only when you lift the laptop screen after sleep/hibernate, or from a cold reboot you have login problems?

---

### Post by pokepal101 on 2010-09-05
its after i lift my laptop screen.

---

### Post by Jose Catre-Vandis on 2010-09-05
Does it go away if you re-enable gdm e.g. undo your edits to stop gdm starting?

You could always uninstall gdm if you don't want it, and just go with startx or use something like slim.

My guess is your problem lies with gdm - somewhere

---

### Post by pokepal101 on 2010-09-05
ill try that, but i need a way to boot to tty1 so i can do startx manually, because a login manager is too slow.

---

### Post by Jose Catre-Vandis on 2010-09-06
You don't need gdm to boot to tty1

---

