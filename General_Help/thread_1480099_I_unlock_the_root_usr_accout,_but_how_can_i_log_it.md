---
title: "I unlock the root usr accout, but how can i log it on?"
date: 2010-05-11
forum: General Help
---

### Post by GoldyW on 2010-05-11
I unlock the root usr accout, but how can i log it on?

---

### Post by zaphod777 on 2010-05-11
in general you don't login to root in a gui session but if you wan't to run as root in the terminal type "su -" and you can then run any program you like from the terminal like "nautilus" if you wan't to browse your file system and make changes. But in gerneral it is a no no. 

typing sudo and then the command will run as root. 

I generally only run as root if I am going to be typing a lot of commands and don't wan't to keep typing sudo.

---

### Post by cdenley on 2010-05-11
You shouldn't authenticate as root. You shouldn't set a root password. Logging into gnome as root creates many unnecessary security risks. If you want a root shell
```

sudo -i

```
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Calash on 2010-05-11
> **GoldyW said:**
> I unlock the root usr accout, but how can i log it on?

I will be echoing the other comments, but it may help to understand your motivations.

Why did you unlock the root account?  Are you following some instructions that said you have to?

---

