---
title: "No permissions during vnc session?"
date: 2010-08-03
forum: General Help
---

### Post by jotok on 2010-08-03
Just got done installing Lucid for a headless server.  I had to set up vnc because for whatever reason vino will not start unless a monitor is plugged in.

I can vnc in just fine.  However, from this session, I cannot make any administrative changes in gnome (e.g. if I open the network settings dialogue, it says "Not authorized to make changes."  If I plug in a thumb drive, I get an "Unable to mount" error).  

I can open a shell and sudo with no problems.

Things that have failed so far:

- Ensured the user was allowed admin in PolicyKit
- Ensured the user is added to the "admin" group, as well as "fuse" and "root"

Googling has just turned up a bunch of frustrated people who also cannot make changes to the system nor mount volumes from VNC, which is odd, because you would think someone else out there would have said "Hey, nobody can actually USE their computer from a VNC session, that's an issue!"  None of the bugs have been resolved, and other threads I have seen have gone unanswered.

So, if anyone has any ideas, I'm all ears.  Thanks!

---

### Post by jotok on 2010-08-05
Bump...nobody else uses VNC?

---

### Post by phantom_ on 2010-12-25
i have the same problem.

i have several drives unmounted (they do not exist in fstab). nautilus cannot mount them displaying an *unauthorized* message.

however, i can mount them under some directory using console (running in the VNC session).

my VNC service is *tightvnc*. no related messages exist in */var/log/syslog*.

---

