---
title: "Secondary user cannot login"
date: 2010-01-02
forum: General Help
---

### Post by feti on 2010-01-02
I have an Ubuntu 9.10 install on a Lenovo laptop. I've been using it for a while and decided to give my son his own login. I added the user through the user and group manager. I set his password as well. Then I changed the login to prompt us for the user and password upon startup. When I try to login with his account, it looks as if it's about to log the account into the system, then shoots me to a very brief shell screen and back to the login prompt. I verified the password right. I even reset it a 3rd time. I can login from the login screen with my account as expected. Is there something I'm missing? The user doesn't have to be part of the admin group in order to login, correct?

Thanks in advance.

---

### Post by zvacet on 2010-01-02
> The user doesn't have to be part of the admin group in order to login, correct?

Yes,that is correct.In fact most of users use second account for every day use and one with admin privileges for updates,packages install,uninstall...

Try to add user from CLI and see if that works.So,from your admin account type in terminal

```
 sudo adduser <username>
```

It will ask you to add new password.so you can put one you used before for that account.

---

