---
title: "Unable to log in as a super user"
date: 2010-04-22
forum: General Help
---

### Post by Skillfullbus on 2010-04-22
Hello All,
Recently I installed Ubuntu using WUBI. During installation it asked for a user name and password which I filled in. That user name and password are the same that I now use to log into ubuntu. But now I am unable to log into super user using the terminal. When I try to log in to the super user account it says that the password is wrong. During the whole installation process only once did wubi ask me to enter password and I am using the same password. My windows user name and password are the same as what I entered during installation. Please help !

Thanks !

---

### Post by jaco223 on 2010-04-22
> **Skillfullbus said:**
> Hello All,
Recently I installed Ubuntu using WUBI. During installation it asked for a user name and password which I filled in. That user name and password are the same that I now use to log into ubuntu. But now I am unable to log into super user using the terminal. When I try to log in to the super user account it says that the password is wrong. During the whole installation process only once did wubi ask me to enter password and I am using the same password. My windows user name and password are the same as what I entered during installation. Please help !

Thanks !

Did you set a password for sudo? 
Open a terminal and type

```
sudo passwd
```

You'll be asked to set a unix password. With this you can login as superuser (sudo).

---

### Post by Skillfullbus on 2010-04-22
Thanks a lot Jaco223 . It worked. Now I am able to log in as a super user using the new password. :)

---

### Post by jaco223 on 2010-04-22
> **Skillfullbus said:**
> Thanks a lot Jaco223 . It worked. Now I am able to log in as a super user using the new password. :)

You're welcome, glad it worked out for you!

Jaco

---

