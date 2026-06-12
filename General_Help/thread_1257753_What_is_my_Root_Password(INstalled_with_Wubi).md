---
title: "What is my Root Password(INstalled with Wubi)"
date: 2009-09-04
forum: General Help
---

### Post by chandru155 on 2009-09-04
I installed Ubuntu with the help of Wubi. It asked me the password for the User account only. But when i tried to login as a root in ubuntu, it shows me in correct password. But i changed my root password via user groups. But i still want to know  what is the root password if i install with the help of Wubi. I also heard that there is some disadvantages of using Wubi. Can anyone tell me what they are?

---

### Post by hetx on 2009-09-04
You  might notice some performance issues. Slower loading, reading, because the harddrive is virtual and on the NTFS partition.

Root is "disabled" in a default Ubuntu install. Activating it is not recommended, but you can google info (I think it has been added into the wiki or something like that now).

If you simply want to run commands as root, using sudo is preferred.

As in:
```
sudo apt-get update
```

This will prompt for user password.

---

### Post by Ms_Angel_D on 2009-09-04
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by chandru155 on 2009-09-04
Guys, I know  these things. Also i know for security purpose, Root is disabled. But i enabled it in LoginWindows-->Security-->Login Local Admin. But when i tried to login(with my user account passwd), it shows my password is incorrect. But i changed the password using User Groups in System-->Admin. But I want to know  what was the root password?

---

### Post by aysiu on 2009-09-04
> **chandru155 said:**
> Guys, I know  these things. Also i know for security purpose, Root is disabled. But i enabled it in LoginWindows-->Security-->Login Local Admin. But when i tried to login(with my user account passwd), it shows my password is incorrect. But i changed the password using User Groups in System-->Admin. But I want to know  what was the root password?
Read this:
[Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Ms_Angel_D on 2009-09-04
We can't tell you this information as it is agains the forums code of conduct if we we're to tell you our accounts would be banned. Please use google to find your information or another linux forum.

---

