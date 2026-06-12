---
title: "sudo takes root password or current user password?"
date: 2009-09-22
forum: General Help
---

### Post by cpthk on 2009-09-22
I thought su command is to execute command via root account. But after I installed fresh ubuntu, I changed root password. I used regular account to do:
```
sudo /etc/init.d/...
```
I putted in root password, but it rejected. I found that it takes current account password, not root.
I was supprised, why is that? If it takes current account password, then any user knows their own password, then everyone has root access?

I thought su stands for switch user, which sudo suppose to switch user to root and do.

---

### Post by sisco311 on 2009-09-22
By default, only users in the admin group are allowed to use sudo.

Please read this for more information:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Chronon on 2009-09-22
Here's info about /etc/sudoers

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

