---
title: "Ubuntu won't restart when multiple users are logged in"
date: 2012-01-01
forum: General Help
---

### Post by dayalsoap on 2012-01-01
Suppose one user is logged in, and then they leave the computer and the screensaver fires.  When another user gets on the computer, they select "switch user" and then log themselves in.  If that user then tries to restart the computer, it won't restart.  It will just sit at the welcome screen.

Notice, nothing is frozen or locked.  I can continually try to restart or shutdown from the login screen, but nothing happens.  If I then log in to the original user, only then does it proceed with the shutdown/reboot.

Why?  How can this be fixed?

---

### Post by mahle on 2012-01-01
That's a bug in the scripting( unless the first user is admin and the second user isn't)..., you should see a warning message telling you that other users are logged in...    report it at launchpad

---

### Post by fdrake on 2012-01-01
are the users both reg users. if the first user is an admin user and the 2nd one is a low level user then this may happen..

---

### Post by dayalsoap on 2012-01-01
> **fdrake said:**
> are the users both reg users. if the first user is an admin user and the 2nd one is a low level user then this may happen..


One user is an admin, and the other is a regular user.  I don't think the order matters, to be honest, from what I've seen. 

One other user said "Report it at Launchpad" --> how do I do that?  Is that something directly through Ubuntu?

---

### Post by PaulW2U on 2012-01-01
> **dayalsoap said:**
> One other user said "Report it at Launchpad" --> how do I do that?  Is that something directly through Ubuntu?

You'll need to create a Launchpad account.

See [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) for help with the bug reporting process.

---

### Post by Tux Aubrey on 2012-01-01
Probably the same bug reported here: 

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/908923](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/908923)

I have this on all my multi-user machines - it doesn't matter whether users are admin or not.

---

