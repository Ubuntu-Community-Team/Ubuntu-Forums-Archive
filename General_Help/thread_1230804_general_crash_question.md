---
title: "general crash question"
date: 2009-08-03
forum: General Help
---

### Post by sdlinux on 2009-08-03
I'm new to ubuntu/linux. I'm running Team Fortress 2 through crossover on Jaunty. It crashes often and causes me to hard power off the computer. Does ubuntu have another way to recover from a crash? A key sequence to return me to the desktop? I didn't expect my windows boot to be more reliable.

---

### Post by think13 on 2009-08-03
You should pretty much always be able to return to a command line using Ctrl+Alt+Backspace, Ctrl+Alt+F1, or Ctrl+Alt+F2.  Once you are there, you should be able to restart GNOME with 

sudo /etc/init.d/gdm restart

Unfortunately, this will close all applications you had open.
If you want to start fresh, you can also use

sudo reboot

from the command line to restart the computer.

---

### Post by lvleph on 2009-08-03
> **think13 said:**
> You should pretty much always be able to return to a command line using Ctrl+Alt+Backspace, Ctrl+Alt+F1, or Ctrl+Alt+F2.  Once you are there, you should be able to restart GNOME with 

sudo /etc/init.d/gdm restart

Unfortunately, this will close all applications you had open.
If you want to start fresh, you can also use

sudo reboot

from the command line to restart the computer.

What logs contain any crash info? My wife's comp keeps crashing and I can't figure out why.

---

### Post by sdlinux on 2009-08-04
> **think13 said:**
> You should pretty much always be able to return to a command line using Ctrl+Alt+Backspace, Ctrl+Alt+F1, or Ctrl+Alt+F2.  Once you are there, you should be able to restart GNOME with 

sudo /etc/init.d/gdm restart

Unfortunately, this will close all applications you had open.
If you want to start fresh, you can also use

sudo reboot

from the command line to restart the computer.

None of those work. My keyboard dies (can't turn off num lock light) when I crash. This is a ps2 keyboard.

---

### Post by lvleph on 2009-08-04
Well, Ctrl+Alt+Backspace is deactivated by default in Jaunty. You would have to reactivate it. I can't remember how to do it, but I am sure you can do a search.

---

### Post by think13 on 2009-08-14
Various logs can be found in /var/log
I the keyboard doesn't even work, that is a very bad crash-I've never had the keyboard stop working.  I guess I would check some of the logs after rebooting and see if anything interesting appears.  Sorry I can't give better advice...

---

