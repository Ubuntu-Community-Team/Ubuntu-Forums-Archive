---
title: "Changing password"
date: 2010-01-12
forum: General Help
---

### Post by minerbog on 2010-01-12
Hi All,

Not sure what happening here but I have just changed my user password via System>Administration>Users.  When I check the password it is the new one, but when I restart the login password and sudo are still the old one but the main keyring password is my new one??

Have I done something wrong??

Thanks.

---

### Post by warfacegod on 2010-01-12
Have you rebooted yet?

---

### Post by sisco311 on 2010-01-12
Try to change your password from System -> Preferences -> About Me or from a terminal:
```
passwd
```

---

### Post by warfacegod on 2010-01-12
> **warfacegod said:**
> Have you rebooted yet?

Please ignore this, I didn't read carefully enough.

Anyway, you can boot into recovery mode, drop to a shell, and use: passwd yourusername to change it.

---

### Post by minerbog on 2010-01-13
> **warfacegod said:**
> Have you rebooted yet?

Yes this was the first thing I tried ;)

---

### Post by minerbog on 2010-01-13
> **sisco311 said:**
> Try to change your password from System -> Preferences -> About Me

Ok Ok,  Somebody please explain this to me.

As you can see from the main post, I changed my password from the System>Administration>Users menu but the login password stayed the same. It was the password that authorized the keys that changed.

I then follow the advice of 'Sisco311' and go to System>Prefs>About Me and change the password (*May I add the screen looks the same!!*). Only to find that this has changed the login password.

Don't get me wrong, I am VERY happy that this is solved :), but can someone please explain how??

Many Thanks.

---

### Post by sisco311 on 2010-01-13
> **minerbog said:**
> Ok Ok,  Somebody please explain this to me.

As you can see from the main post, I changed my password from the System>Administration>Users menu but the login password stayed the same. It was the password that authorized the keys that changed.

I then follow the advice of 'Sisco311' and go to System>Prefs>About Me and change the password (*May I add the screen looks the same!!*). Only to find that this has changed the login password.

Don't get me wrong, I am VERY happy that this is solved :), but can someone please explain how??

Many Thanks.

It's a BUG: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/490093](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/490093)

If you have a few minutes, please register at Launchpad to confirm the BUG.

---

