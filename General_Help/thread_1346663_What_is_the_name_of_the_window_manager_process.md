---
title: "What is the name of the window manager process?"
date: 2009-12-05
forum: General Help
---

### Post by mahela007 on 2009-12-05
What is the name of the Window manager process in gnome? I want to try stopping it using the terminal for educational / experimenting purposes. ;-)

---

### Post by oldos2er on 2009-12-05
gdm

---

### Post by mahela007 on 2009-12-05
How can I find the PID of the gdm process? I tried using ```
top
``` but I can't figure out how to use```
 |grep
``` with this command to search for gdm.
 Should there be a process called gdm?

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
What are you trying to do with gdm? To restart it use ```
sudo /etc/init.d/gdm restart
``` or to stop it replace restart with stop and start the same way.

Not sure if you want the Window manager or desktop manager. GDM is the desktop manager and nautilus is the window manager.

---

### Post by falconindy on 2009-12-05
> **Sin@Sin-Sacrifice said:**
> What are you trying to do with gdm? To restart it use ```
sudo /etc/init.d/gdm restart
``` or to stop it replace restart with stop and start the same way.

Not sure if you want the Window manager or desktop manager. GDM is the desktop manager and nautilus is the window manager.
You should check your facts, first.

GDM is an upstart job now. You should be using 'sudo service gdm restart' to handle GDM.

GDM is your login manager. It facilitates communication between the GUI and PAM, which is an authentication module. You can bypass GDM by logging in through a tty and using startx.

Nautilus is just a file browser. Yes, it has some hooks into the rest of the environment, but this is merely integration to give the end user a cleaner experience.

Ubuntu's window manager is either Compiz or Metacity. A window manager is nothing more than a set of programs that allows you to manipulate (move/resize) the windows created by programs. You can absolutely have a GUI without a window manager, but it won't be very friendly.

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
Entschuldigen Sie bitte...

---

### Post by oldos2er on 2009-12-05
> **falconindy said:**
> GDM is an upstart job now. You should be using 'sudo service gdm restart' to handle GDM.

 The OP is using 9.04.

---

### Post by mahela007 on 2009-12-06
No... I'm actually using 9.10 (I have to update my profile on these forums). I want to restart the window manager. Should I look for a process called metacity? I couldn't find anything like that by typing 'top' at the command line.

I found Compiz. Will ubuntu use compiz as the default from 9.10 onwards?

---

### Post by foureyesboy on 2009-12-06
I think the default window manager is metacity, but if System>Preferences>Appearance>Visual Effects is turned on, I think compiz will take over.

Usually when I want to restart the X Window session, I will just go for sudo service gdm restart at a tty session.

---

