---
title: "Gnome-do Hanging System and Login"
date: 2010-06-16
forum: General Help
---

### Post by bg1256 on 2010-06-16
I'm running a fresh install of Lucid without any issues thus far. I have my computer setup to log me in automatically, without requesting a password.

I installed Gnome-do and set it up to run at login (as I always have). After a reboot, my system is not responding to input from my mouse or keyboard. I can move my cursor, but it will not accept input.

I see gnome-do, which is partially covered by the "Unlock keyring" dialog" (which always comes up, I think to unlock my wifi).

Does anyone know a fix without wiping the system?

---

### Post by bg1256 on 2010-06-16
Wouldn't you know it. I solved it almost immediately after posting.

The way I did it:

Boot up your computer and hold Shift, which brings you to the GRUB menu.

Select recovery mode.

Select the root shell option (networking doesn't matter)

When you get to a terminal as root, simply run

```
apt-get remove gnome-do
```

to remove Gnome-Do.

Apparently, Gnome-Do can only be run manually if you have your machine set to login automatically. ):P

---

