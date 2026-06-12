---
title: "unable to log in as any user"
date: 2010-08-28
forum: General Help
---

### Post by CyberJacob on 2010-08-28
I first noticed the problem when sudo constantly told me that my password was incorrect, I tried changeing it but it still said that, I decided to reboot the system and now cannot log in as any user. through a terminal is is reported as an incorrect password and an authentication failure when using gnome. however I know the password is correct. I have tried creating a new user but cannot login with that account either. the only way I can access the system is to boot into single user mode. I checked the /etc/passwd and /etc/sudoers files and those are both correct.

---

### Post by zpletan on 2010-08-28
If you boot into single user mode and run:
```
passwd <username>
```
Where <username> is, obviously, your username.
Can you log in now?

---

### Post by CyberJacob on 2010-08-28
that's how I changed my password before, so no

---

