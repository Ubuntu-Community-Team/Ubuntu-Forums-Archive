---
title: "How to execute a script on X shutdown?"
date: 2010-03-27
forum: General Help
---

### Post by kriukov on 2010-03-27
I would like to be able to execute a script every time X is shut down (e.g., by Ctrl+Alt+Backspace), namely, logout. Is this possible? If it is, in what file do I put the command/script?

---

### Post by kriukov on 2010-03-30
bump?

---

### Post by prodigy_ on 2010-03-30
Are you using Gnome? If yes, place your logout script in:
```
/etc/gdm/PostSession/Default
```

I'm not sure if it'll work with Ctrl+Alt+Backspace though.

---

### Post by Penguin Guy on 2010-03-31
> **prodigy_ said:**
> Are you using Gnome? If yes, place your logout script in:
```
/etc/gdm/PostSession/Default
```

I'm not sure if it'll work with Ctrl+Alt+Backspace though.
Hi, I've got a script that changes the background and would like to run it at shutdown. I just saw your post on Google and was wondering if there was any way to do something like this as a normal user?

---

### Post by prodigy_ on 2010-04-03
> **Penguin Guy said:**
> Hi, I've got a script that changes the background and would like to run it at shutdown.
Try gnome-schedule: ```
sudo apt-get install gnome-shedule
```

---

### Post by Penguin Guy on 2010-04-03
> **prodigy_ said:**
> Try gnome-schedule: ```
sudo apt-get install gnome-shedule
```
That only has an 'on reboot' option - which won't work for what I'm trying to do. My script must be run when the system is shutting down (not when it is rebooting or starting up).

---

### Post by prodigy_ on 2010-04-03
> **Penguin Guy said:**
> That only has an 'on reboot' option - which won't work for what I'm trying to do. My script must be run when the system is shutting down (not when it is rebooting or starting up).
You can place a script into **/etc/init.d** and a symlink to the script into **/etc/rc0.d**. It'll be executed only at shutdown, albeit with root privileges.

---

### Post by falconindy on 2010-04-03
> **kriukov said:**
> I would like to be able to execute a script every time X is shut down (e.g., by Ctrl+Alt+Backspace), namely, logout. Is this possible? If it is, in what file do I put the command/script?

ctrl-alt-bksp sends a kill -15 to X's PID. It's probably shutting down gracefully, but not via the normal means. Why not make a new keybinding (e.g. ctrl-super-bksp) that runs your script (which kills X in the process)?

---

### Post by Penguin Guy on 2010-04-04
> **prodigy_ said:**
> You can place a script into **/etc/init.d** and a symlink to the script into **/etc/rc0.d**. It'll be executed only at shutdown, albeit with root privileges.
I tried that, but it needs to be run inside the user's X session or it cannot view/change gconf settings.

---

### Post by kriukov on 2010-04-12
The thing is, I don't use gdm but I would like the script to be executed whenever I kill X. Do I have to edit /usr/bin/startx?

---

### Post by dcstar on 2010-04-13
> **prodigy_ said:**
> Are you using Gnome? If yes, place your logout script in:
```
/etc/gdm/PostSession/Default
```

I'm not sure if it'll work with Ctrl+Alt+Backspace though.

That is incorrect for later Ubuntu releases. That code will only get executed on logout as GDM Shutdown/Restart immediately kills the GDM and X session without giving that script an opportunity to run.

It is a real PITA as things like the Shutdown Sound is now really only a "Logout" sound.

---

### Post by ryu kun on 2010-09-18
No solution?

---

