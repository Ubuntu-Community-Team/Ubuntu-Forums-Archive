---
title: "remote session, best way?"
date: 2010-09-17
forum: General Help
---

### Post by Cue2 on 2010-09-17
What is the best way of running programs from a remote system? I use to use ssh with x forwarding but found that I could not open files from a samba share from the forwarded app. So I switched to a weird way of using vnc. I would ssh to the remote system, run 'vnc4server -geometry 800x480' so that the res matches my local machine then connect by vnc to run 'gnome-session'.
Most things worked fine as if I were at the local machine but it also had some odd behaviour in some apps, not sure why. so is xdmcp the least troublesome way of doing this?

---

