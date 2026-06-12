---
title: "Users"
date: 2011-05-28
forum: General Help
---

### Post by ladlers on 2011-05-28
How do you create and log onto new users in 10.10? Is it possible to change the user that logs on at startup?

---

### Post by nzjethro on 2011-05-28
Check out:
[http://www.jonathanmoeller.com/screed/?p=2572](http://www.jonathanmoeller.com/screed/?p=2572)

Otherwise, I think
```
sudo adduser <username>
```
does the trick, and follow the prompts from there. Good luck.

---

### Post by ladlers on 2011-05-29
Then how do you log onto the user? Also, how do you set the user to start when booting?

---

### Post by JRV on 2011-05-29
To add a user click on System in the upper right corner.
Click on Administration.
Click on Users and Groups.

To select a user to auto login click on System in the upper right corner.
Click on Administration.
Click on Login Screen.

---

### Post by nzjethro on 2011-05-29
> **ladlers said:**
> Then how do you log onto the user? Also, how do you set the user to start when booting?
 
It should come up as an option when you boot up. On the logon page, you should have the option to "Log on as a different user". Click that, and select your new user.

---

