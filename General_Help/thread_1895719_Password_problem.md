---
title: "Password problem"
date: 2011-12-15
forum: General Help
---

### Post by DeaDZ_Will on 2011-12-15
Hey guys, 
Basically this has happened:
I have no password but it asks me for a password to do administrative things, help!

---

### Post by DeaDZ_Will on 2011-12-15
> **pastagage said:**
> Can you leave the pwd blank ?

No it doesn't let me, neither does it let me still use the old one, I've tried admin administrator and none of it works.
P.s. sorry I'm usually much more Hospitable but I have had no sleep recently due to college work, I guess it's no excuse though :(!

---

### Post by community on 2011-12-15
You were asked to type a password during the installation,right?
If that doesn't work open the terminal and type sudo -i .Now look whether you got the root privilege or not?If yes then type passwd <username>.Now it will ask for a new password.Type it and confirm the same.

---

### Post by snowpine on 2011-12-15
You can set/change your password using the following terminal command:

```
passwd
```

---

### Post by lisati on 2011-12-15
When you get a popup like that, typing in the same password that you use to login to your system usually will be adequate.

---

### Post by DeaDZ_Will on 2011-12-15
> **snowpine said:**
> You can set/change your password using the following terminal command:

```
passwd
```

This, perfect, thankyou so much :)

---

