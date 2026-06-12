---
title: "GDM Password Prompt Missing"
date: 2012-09-17
forum: General Help
---

### Post by hbj on 2012-09-17
I have a strange problem.  We are running Ubuntu 12.04.1 with NFS-mounted home directories and Kerberos authentication.  Most of the time everything works fine.  However, occasionally on logout, GDM does not return to the login prompt.  It just shows the computer name where normally it would show a list of users.  There is no way to select or enter a user to log in.  Restarting GDM doesn't have any effect - still no login prompt, and the only solution seems to be rebooting.  Any ideas?

---

### Post by hbj on 2012-10-09
This happened again to me twice today.  Any ideas?

---

### Post by hbj on 2012-11-02
In case anybody else runs into this problem, I found a workaround by switching to KDM instead of GDM.  It hasn't happened since.

---

