---
title: "Change the sudo password?"
date: 2006-04-16
forum: General Help
---

### Post by elamericano on 2006-04-16
Is there a way to change the sudo password so that it's not the same as my user password? I'm thinking if my user account password gets compromised, then they'll have root access through sudo. I might be better off to disable sudo and open a root session when I need to do elevate my priviledges.

---

### Post by localzuk on 2006-04-16
No, as the password for sudo is your own password - it is not really a security check, more a 'are you sure you want to run this as root' check.

If you are worried about this, the simplest thing to do is create a non-privileged user and use that for normal work and only use your sudo privileged account when you want to do admin stuff. This is simpler than disabling sudo and enabling root IMO.

---

### Post by Qrk on 2006-04-16
What you want, essentially, is the "normal" mode for user accounts on Linux. This has a "root" account and a "user" account with different passwords. 

Even if you enable root in ubuntu, (not a good idea) the passwords prompted when doing configuration will be your own, not the root password. 

To make sudo ask for the root password, do a:
```
sudo passwd root
```
enter in your user password,
then enter what you want the root password to be and repeat.

```
sudo gedit /etc/sudoers
```

Scroll down to the line "Defaults" (should be line 12) and add ```
rootpw
``` to the line.

**I do not recommend that, because everyone I have talked to thinks that the default ubuntu way is more secure. Also, messing around with sudoers can be a recipe for disaster. If the file is  lost or edited out of syntax, you can loose sudo user permissions entirely.**

---

### Post by elamericano on 2006-04-16
Thanks for the warning. I've lost sudoer before by changing its permissions - best way to learn how to recover from that. ;-)

---

