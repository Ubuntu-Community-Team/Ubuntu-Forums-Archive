---
title: "Can not set root password at any time!!!"
date: 2004-10-20
forum: General Help
---

### Post by largede on 2004-10-20
I am somewhat new to linux and for the last three months have been getting used to the OS and trying out many diffent distros on several diffent computers (new and old).  
    I have found that so far ubuntu is the best distro who's current relese works awsome on older hardware (I buy old stuff at yard sales and thrift stores and get them going for people that can't afford a new box).
     My problem is that upon install I don't get any option to set the root password and I can't figure out how to do it after install.  The fix is probably out there if I keep searching but being a new father I don't really have but a half hour a day after work to much.
     Any input would be awsome.  Thanks in advance.  Dust

---

### Post by Rancoras on 2004-10-20
The root account is disabled by default.  Anything you normally did as root with other distros, you do with sudo in Ubuntu.  When you are prompted for the password, use the password to the account you created during install.

---

### Post by FLeiXiuS on 2004-10-20
```
sudo passwd root
```

This should enable you to set the root password!

---

