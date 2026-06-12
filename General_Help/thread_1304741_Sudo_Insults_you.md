---
title: "Sudo Insults you?"
date: 2009-10-29
forum: General Help
---

### Post by teward on 2009-10-29
I've seen people configure their sudo commands to insult the user when the wrong password is entered.  Anyone know how to configure this (if possible)?

---

### Post by y@w on 2009-10-29
This page should get you in the right direction:

[http://blog.zloether.com/2009/09/customize-your-etcsudoers-file.html](http://blog.zloether.com/2009/09/customize-your-etcsudoers-file.html)

---

### Post by sisco311 on 2009-10-29
Edit your sudoers file:
```
sudo env VISUAL=gedit visudo
```

and append the *Defaults* line with *insults*

```
Defaults	env_reset**,insults**
```

save the file and exit.

test it:
```
sudo -K
```
```
sudo echo insert wrong password
Password: 
It's only your word against mine.

```

---

### Post by teward on 2009-10-29
Sweet.  Thanks for the help.

---

### Post by wilee-nilee on 2009-10-29
Is this the masochistic method.

---

