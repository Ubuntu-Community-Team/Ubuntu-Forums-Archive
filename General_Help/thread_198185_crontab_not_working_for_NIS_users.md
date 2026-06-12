---
title: "crontab not working for NIS users"
date: 2006-06-16
forum: General Help
---

### Post by BrianK on 2006-06-16
The crontab doesn't run for my NIS users.  It works fine for local users (though the only local users I have are root & the inital user which I never use)

What do I need to do to make their crontabs run?

This is Ubuntu 6.06 server.

---

### Post by BrianK on 2006-08-08
From another thread, use PAM:

Just Add
auth optional pam_group.so
to /etc/pam.d/common-account

and
"*;*;*;Al0000-2400; audio,floppy,video,cdrom,plugdev"
to /etc/security/group.conf (add to list as necessary)

---

