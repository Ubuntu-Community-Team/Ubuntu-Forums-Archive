---
title: "sudo options"
date: 2009-09-01
forum: General Help
---

### Post by SuperSonic4 on 2009-09-01
Is there any way I can put sudo into a bash script so that it can run as root while I am away from the PC?

This would be for a sudo make install step

---

### Post by denver on 2009-09-01
hmmmm...i think you could try something allong the lines of:

```
sudo sudoedit /etc/sudoers
```

and add the following lines at the end:

```
Cmnd_Alias NO_PASS_COMMANDS = /usr/bin/make
username ALL= NOPASSWD: NO_PASS_COMMANDS 
```

This should allow you to run:

```
 sudo make <whatever>
```

without a password.

NOTE: Replace "username" with your actual user. Please make sure you test this before creating your scripts and leaving :). It's been a while since i wrote sudo rules.

---

