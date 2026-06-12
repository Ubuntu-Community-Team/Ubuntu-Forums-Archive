---
title: "Need to login to root, sudo -s does not work"
date: 2009-11-12
forum: General Help
---

### Post by JessicaSideways on 2009-11-12
Hello,

We need to gain root access to our Xubuntu installation because we need to install LIRC files to get our remote control to work (we are using it for a media centre). So how do we get into root since sudo -s does not work for us.

Furthermore, we cannot seem to login to root even though we created an user account for it and enabled a random password for it, which we copied down and it would not take.

Sincerely,
Jessica Sideways

---

### Post by limabean on 2009-11-12
When you use "sudo -s", you use your standard user password that you would normally use for sudo, not the root one you created.

---

### Post by niteshifter on 2009-11-12
Hi,

Try:
```
sudo -i
```

in a terminal to get a root shell.

---

### Post by iruel on 2009-11-12
use this
```
sudo su
```
;)

---

### Post by aysiu on 2009-11-12
```
sudo -i
``` or ```
sudo su
``` will work and ask for your **user** password (there is no root password in Ubuntu by default).

**Never** use *sudo -s*

---

### Post by lisati on 2009-11-12
Potentially useful reading when talking about admin privileges and sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

