---
title: "Login password"
date: 2012-08-05
forum: General Help
---

### Post by vichor on 2012-08-05
Hi all,

Few weeks ago I upgraded up to Pangolin and now the login screen is not asking my password. Don't get me wrong, it is not automatically login, it just presents the login screen with the users list and, where the passsword should be entered there is a "click to login" button.

The funny thing is that later, once in my session, it asks my password to unlock the keyring, to sudo things, etc.

Any idea anyone?

---

### Post by sisco311 on 2012-08-05
Users who are in the **nopasswdlogin** are allowed to log in without a password.

---

### Post by vichor on 2012-08-07
That was it. Thank you!! 

I have no idea how my user ended up in that group.

Just for reference in case any other stumbles upon here, to fix this you have to edit /etc/group
```

$ sudo gedit /etc/group
```

search for nopasswdlogin and remove the desired users from there. In other words, look for

```
nopasswdlogin:x:121:<list of users>
```

and remove from the list the user you want to have password on login.

---

