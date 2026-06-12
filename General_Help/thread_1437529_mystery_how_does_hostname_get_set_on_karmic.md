---
title: "mystery: how does hostname get set on karmic"
date: 2010-03-24
forum: General Help
---

### Post by ntucker on 2010-03-24
I just set up a new karmic server, and the hostname is being set properly, but I'm not exactly sure how, since there is no longer an init script that sets it (it used to be /etc/init.d/hostname.sh on my older servers).  Now I'm curious: what is the new mechanism by which the server's hostname is set at boot time?

---

### Post by john newbuntu on 2010-03-24
Ask the Oracle: "man hostname"

---

### Post by ntucker on 2010-03-24
I'm not sure you understand the question.  Used to be, there was a script, /etc/init.d/hostname.sh, which read the file /etc/hostname, then called 'hostname' (the program you mention) in order to actually set the hostname.  Who calls 'hostname' now?  None of the rc scripts do it, so how does it get done?

---

### Post by john newbuntu on 2010-03-24
To detail it more, Ubuntu uses upstart mostly and is trying to get away from the old System V init scripts.  You should see a hostname.conf job that sets the hostname from the files you mentioned at boot time.

---

