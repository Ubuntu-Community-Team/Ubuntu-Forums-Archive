---
title: "sudo isn't asking for password"
date: 2010-07-27
forum: General Help
---

### Post by Turpin on 2010-07-27
I installed ubuntu minimal install with xorg, lxde, and lxdm  During the manual install, I do remember it asking something about extra encryption on password or something like that which was "highly recommended" and I chose yes, which probably has nothing to do with my problem, which is: Whenever I run something in the terminal with sudo, it just opens without asking for password.  What did I do wrong?  How might I fix this?  Thanks.

---

### Post by sisco311 on 2010-07-27
Please post the output of:
```
sudo -k cat /etc/sudoers
```
and 
```
groups
```

---

### Post by limestone on 2010-07-27
try reboot, Ubuntu may have saved root passw for session..

---

### Post by Turpin on 2010-07-27
lol yep.  Thanks. I just rebooted, tried sudo on something and it did prompt me for it this time.  It was either what you said or I should mention I also did a "sudo passwd root" and "sudo passwd myusername". Those probably had nothing to do with it.
Sisco, I just saw your post.  I'll check those out as well just to make sure things on this system match my other system which I believe to be set up properly.

---

### Post by sisco311 on 2010-07-27
If the invoking user is root or if the target user is the same as the invoking user, no password is required.  Otherwise, sudo requires that users authenticate themselves with a password by default (NOTE: in the default configuration this is the user's password, not the root password).
Once a user has been authenticated, a time stamp is updated and the user may then use sudo without a password for a short period of time (15 minutes unless overridden in sudoers).

**sudo -k** invalidates the user's timestamp by setting the time on it to the Epoch.  The next time sudo is run a password will be required.

See ```
man sudo
```

---

### Post by Turpin on 2010-07-27
Thanks everybody.  :)

---

