---
title: "Can't ssh into new user."
date: 2010-02-17
forum: General Help
---

### Post by Benkrishman on 2010-02-17
I've just set up a new user on my ubuntu machine that I plan to setup a git repo on for classwork.  I created a new user(git) and attempted to log into it using ssh, but keep getting denied when I enter the password.  For some background info, I've been using ssh to connect to this ubuntu box with no problems on the main user account however, after setting up the new user(using 'sudo adduser git') and trying to login I'm denied every time I enter the password(which I know is correct because I just created it).


Am I doing something wrong setting up the new user, or missing something between creating it and logging in?  Any help would be greatly appreciated.

Thanks

(solved, allowed users in sshd_config, sorry for the waste of a thread)

---

