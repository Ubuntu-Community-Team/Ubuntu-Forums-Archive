---
title: "Multiple gnome-keyring-daemon instances running"
date: 2012-06-14
forum: General Help
---

### Post by citrusmoose on 2012-06-14
I've been noticing this for a few releases now.  Every time I log in (without rebooting), I get a new instance of gnome-keyring-daemon (/usr/bin/gnome-keyring-daemon --start --foreground --components=secrets) when it's called upon (via dbus I assume).  It appears that the previous instances never get killed when I log out.  It doesn't appear to affect anything, but it'd be nice not to have all those processes running for no reason.  Google/the forums can't seem to find anybody with the same issue.  Anybody know what's going on?

Running Xubuntu 12.04 x86_64.

---

### Post by citrusmoose on 2012-06-18
Bump

---

### Post by wheeze on 2012-06-18
I had that problem when I ran gnome-keyring under MATE. mate-keyring performed as expected, only one instance, but is broken in some ways. I have since switched over to Cinnamon and gnome-keyring behaves normally. Cinnamon is based on GNOME 3.

I always attributed the gnome-keyring behavior to have something to do with running under MATE, but maybe it's something to do with running under a non-GNOME DE?

---

