---
title: "Prompt to change username and password"
date: 2010-09-02
forum: General Help
---

### Post by bert682 on 2010-09-02
Hey guys

So I am sending my sister my old laptop with ubuntu netbook remix installed.  I have created and username and password as required when installing.  Is it possible to prompt the user to change these when they login?

I dont think my sister could understand how to open up the terminal and issue commands.

Regards, Robert

---

### Post by dcstar on 2010-09-02
> **bert682 said:**
> Hey guys

So I am sending my sister my old laptop with ubuntu netbook remix installed.  I have created and username and password as required when installing.  Is it possible to prompt the user to change these when they login?

I dont think my sister could understand how to open up the terminal and issue commands.

Regards, Robert
Do this and they will be prompted for a new password at login:
```
sudo passwd -e *username*
```

---

### Post by lisati on 2010-09-02
Another possibility would be to do an OEM install. I haven't used it for a while, but the last time I had a look it let me install a bunch of software, updates, etc, and next boot it asked for a new user name & password.

---

