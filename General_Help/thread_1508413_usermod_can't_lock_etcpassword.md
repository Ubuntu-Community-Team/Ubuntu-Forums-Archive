---
title: "usermod: can't lock /etc/password"
date: 2010-06-12
forum: General Help
---

### Post by alem189 on 2010-06-12
I'm trying to start the fluidsynth MIDI program, and it's asking me to run 'usermod -a -G audio username' to configure it correctly. However, when I try that, it says: ```
usermod: cannot lock /etc/passwd; try again later.
```
I've rebooted multiple times, and it still persists. Is there a way to fix this or achieve this another way?

---

### Post by dcstar on 2010-06-12
> **alem189 said:**
> I'm trying to start the fluidsynth MIDI program, and it's asking me to run 'usermod -a -G audio username' to configure it correctly. However, when I try that, it says: ```
usermod: cannot lock /etc/passwd; try again later.
```
I've rebooted multiple times, and it still persists. Is there a way to fix this or achieve this another way?

```
man sudo
```

And you do know that "username" means **your** username?

---

### Post by alem189 on 2010-06-13
Wow, that was stupid of me...:oops:

---

