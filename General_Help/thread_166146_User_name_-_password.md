---
title: "User name - password?"
date: 2006-04-25
forum: General Help
---

### Post by Chypara on 2006-04-25
Anybody can help me, I bought computer in Mercy House with Ubuntu installed and there is a user name and password protected. How I can see, this is interesting os and I like to try it, but is there any way to get in without knowing a user name and password??:confused:

---

### Post by mjm115 on 2006-04-25
Mercy House may have that information.  If you did not install Ubuntu yourself, then unfortunately you will not be able to log on to the system.

---

### Post by jazzmuzik on 2006-04-25
Talk the the previous owner. Or just reinstall Ubuntu. It's free.

---

### Post by sinkxdie on 2006-04-25
Whats a Mercy House?

---

### Post by aysiu on 2006-04-25
Boot into recovery mode and ```
adduser chypara admin
```

---

### Post by Toxicity999 on 2006-04-26
Agreed, once you add a user you can play with some options to get the other account back. Chances are it's something stupid set for the u/p that they use on all installs... assuming I can geuss at what you even got it from.

---

### Post by Ramses de Norre on 2006-04-26
In recovery mode:

```
ls /home/
```
Should reveal the username of the existing user (there will be a folder with his username in /home/)
```
passwd username
```
To set a new password for that user.
You can login with that information.

---

