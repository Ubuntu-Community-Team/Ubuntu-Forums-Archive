---
title: "How do I change the root password"
date: 2012-03-02
forum: General Help
---

### Post by Ewe Loon on 2012-03-02
How do I change the root password

or how can I verify I am Entering it correctly

---

### Post by Gremlinzzz on 2012-03-02
you can change it in terminal type in:popcorn:

passwd

---

### Post by nothingspecial on 2012-03-02
See here

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Paddy Landau on 2012-03-02
No, no, no. You don't want to change the root password. This breaks the security model in Ubuntu. You never, ever, need to log in as root in Ubuntu.

If you need to enter commands as root, pefix the commands with sudo, e.g.
```
sudo apt-get update
```If you want to run a GUI program as root, prefix the command with gksudo, e.g.
```
gksudo nautilus
```

---

### Post by Ewe Loon on 2012-03-03
Thankyou all, that was the info i needed, even though not what i asked for

---

### Post by Paddy Landau on 2012-03-03
> **Ewe Loon said:**
> Thankyou all, that was the info i needed, even though not what i asked for
The forum T&C does not permit us to tell you about changing the root password as that breaks the security model. In fact, I only found out how (by accident) about two years after starting to use Ubuntu.

---

