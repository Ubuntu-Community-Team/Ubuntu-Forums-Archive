---
title: "Cannot login to Lubuntu 11.10"
date: 2012-03-09
forum: General Help
---

### Post by sssjkn on 2012-03-09
I use Lubuntu 11.10, and from a few days ago, attempts to login fail. After entering my password, the field disappears, and then the user field reappears, as if an incorrect login (which is not the case because I can login to the tty fine).

I have tried fscking, upgrading packages, deleting .Xauthority, reinstalling lxdm, reinstalling openbox.

Please help me...

---

### Post by winh8r on 2012-03-09
Can you try logging in via tty and creating a new user account and password, then see if you can login normally to the new account?

That might indicate whether the problem is with only your login credentials at the default login screen or the login system itself.

```
sudo adduser yournewusername
```

---

### Post by sssjkn on 2012-03-09
No good, shows the same symptoms.

---

