---
title: "ubuntu 10.04 ask for the password after  hibernate"
date: 2010-05-08
forum: General Help
---

### Post by ramire on 2010-05-08
i dont need the password after hibernate,how i can disable request it
in administration-login window selected auto login my name
tnx

---

### Post by P4man on 2010-05-08
press alt+f2 and run 

```
gconf-editor
```

browse to

/apps/gnome-power-manager/lock/hibernate

Disable it.

---

### Post by ramire on 2010-05-08
> **P4man said:**
> press alt+f2 and run 

```
gconf-editor
```

browse to

/apps/gnome-power-manager/lock/hibernate

Disable it.


thank you. work

---

### Post by CROLMAC on 2010-07-13
I am a bit confused when I try to apply some fixes ( always simple, never complicated, I am aware of my limitations), because I always have the impression that for some reason the ubuntu that I am using is never the same as the one other people use. My limitations, I'm sure. 
  I tried the fix in this reply, and I got the error window "could not open location 'file:///home/crolmac/gconfig-editor' and it goes on stating there exists no such file or directory. 
  I am probably not choosing the right boxes, could someone please guide me? I have removed the password from my login, and this software ridiculously insists on imposing it on me every time I want to resume from the screensaver, let alone hibernate. thanks for your patience.

---

### Post by CROLMAC on 2010-08-31
i just realised i didn't reply here: this solution didn't work. I retried it, found what seemed right, and nada

---

### Post by juil on 2010-08-31
CROLMAC, are you reading the posts?

You have to type 'gconf-editor' as P4man pointed out, not 'gconfig-editor'

If ALT+F2 doesn't work, just open your terminal and type the command. It won't ask you for your password. At least it didn't for me.

---

