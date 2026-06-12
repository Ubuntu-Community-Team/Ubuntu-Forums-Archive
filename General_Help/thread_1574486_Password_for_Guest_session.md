---
title: "Password for Guest session"
date: 2010-09-14
forum: General Help
---

### Post by deckoff on 2010-09-14
I enter guest session and try to install an app. I am asked for a password, I try with mine (for my account) but it seems to be incorrect(logical). well how can I find the password for the guest account???

---

### Post by robsoles on 2010-09-14
I haven't tried to muck around with a password for the guest session so I can't help you get or set it at this point but you pique my curiosity.

Why do you want to install an app as guest?

---

### Post by deckoff on 2010-09-17
Well I want to try a new theme, and to add it is as ppa, so it requires sudo , hence I need password :):). Installed it on my main account, but anyway might be useful to know it

---

### Post by robsoles on 2010-09-17
I haven't tried due it is sort of against the point of a 'guest' user but if you assign them a password and then make them a member of 'wheel' and maybe a couple of other groups then your guest should be able to 'sudo' but it really does defeat the purpose of a guest account and it may not be valid:

(in terminal)
```
sudo 'passwd guest'
```

If that executes without error and allows you to set a password for 'guest' then it should be possible to grant them 'sudo' privileges although it really does seem nutty to me to pursue that.

If you don't want something installed via your main account on your own PC then it isn't against the rules to make yourself a secondary account and allow that account 'sudo' privileges - it should be against the rules to allow the guest more than 'guest' privileges.

---

