---
title: "Start daemon on login"
date: 2011-08-11
forum: General Help
---

### Post by jonatanschroeder on 2011-08-11
I'm creating a script that I want to run every time any user logs in (not only on the GUI, but also via SSH or via text terminal). The script will check if a daemon program is running (one per user or per session, haven't decided yet) and, if it isn't, will start it. I want this to be system-wide, not per-user. I thought about using /etc/profile (or creating a file in /etc/profile.d/) for CLI logins and /etc/X11/Xsession (same remark, Xsession.d) for GUI logins. My problem is that if the user uses a non-Bourne shell (e.g. TCSH) this won't work. Any suggestions? Is there any initialization script that is run no matter what shell the user has?

---

### Post by LowSky on 2011-08-11
what is the script supposed to be doing? I would add it to /etc/init.d to run from boot and not from login. that way it is always running in the background, no matter the user or method of login.

---

### Post by jonatanschroeder on 2011-08-11
It is a possibility if I change the behaviour of my daemon. What I need right now is an instance per user, not a single instance for all users. But if I don't find a way to do it per user, I'll probably do some workaround with a generic instance.

---

