---
title: "update problem"
date: 2006-05-12
forum: General Help
---

### Post by dcc on 2006-05-12
I have been running Ubuntu 5.10 on a second laptop for a couple months with no problems. I have accepted any updates as they were offered from icon in teh upper right toolbar. It is now telling me that 3 updates are available. When I click on the icon, and enter my password, I get the message below.

Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.

I get this even after rebooting, and going straight to the updates. I am running a default installation, except for updating Firefox, using a script from this forum. I have used differant distros of Linux for a while now without virus or spyware protection. Does this suggest that something has infected my system, or does this point more to a bug in the update manager? A reinstall would not be a problem, but I would like to know what is causing this. Any suggestions?
dcc is online now   	Edit/Delete Message

---

### Post by tonyr on 2006-05-12
I doubt very seriously that a virus is involved.  After a fresh boot, not starting
any programs, in a terminal do this:
```

ls -l /var/lib/apt/lists/lock
ls -l /var/lib/aptitude/lock
ls -l /var/cache/apt/archives/lock

```

Each one of those is a lock file. An application like **aptitude** or **synaptic**
creates a link to some of those files by opening them.  If there are any applications running that
are using any of those files, the link count will be greater than 0.  Here is an
example from my machine:
```

ls -l /var/lib/aptitude/lock
-rw-r----- 1 root root **0** 2006-04-09 15:46 /var/lib/aptitude/lock
ls -l /var/cache/apt/archives/lock
-rw-r----- 1 root root **0** 2006-05-12 10:47 /var/cache/apt/archives/lock
ls -l /var/cache/apt/archives/lock
-rw-r----- 1 root root **0** 2006-05-12 10:47 /var/cache/apt/archives/lock

```

The bold **0** in each report line is the link count for that file.  If any one of those
is not zero, something is either running, or the directory entry for that file
is in error.  

I don't know whether GNOME has session memory, but in KDE, login sessions are
remembered and re-established on subsequent logins.  You should try to see
if any **apt** related process got restarted at login.  In a terminal do
```

ps aux | grep apt

```
and see if anything pops out.

---

