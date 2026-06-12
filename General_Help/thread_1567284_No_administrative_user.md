---
title: "No administrative user"
date: 2010-09-03
forum: General Help
---

### Post by mario.r on 2010-09-03
Hi

I'm a newby and struggling with a netbook which I received with Ubuntu 8.1 on it.  This netbook only has a user with non-administrative privs on it and root user but I do not have root's password.

Is there a way that I can create a new administrative user of change the current user's group so that it can do sudo commands or have more privs?

Thanks

---

### Post by gzarkadas on 2010-09-03
You can reboot and enter single user mode (choose a kernel that has recovery or something similar in its name - I haven't interfaced with Ubuntu versions older than Karmic).

Edit:
But first try to execute a "sudo something" command with the unprivileged account (say `sudo ls -l /etc/shadow'). sudo is used a long time in Ubuntu; maybe there is no real issue here.

---

