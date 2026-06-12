---
title: "I can't type out the root user's password"
date: 2009-07-25
forum: General Help
---

### Post by kart168 on 2009-07-25
Hello!

i've newly installed ubuntu 9.04 since i'm very much interested to use linux:D. While reading some books on linux i found that there is a term mentioned called the root user. I'm the only user to my system . So it means i'm the root user? and moreover if i typed the su command in the terminal i couldn't type my password to avail the superuser status........pls help me with this problem...:-?


thank you,

---

### Post by SuperSonic4 on 2009-07-25
Root is disabled in ubuntu in favour of using sudo to temporarily gain root access - see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more info

You *can* enable the root account but you'll have to google it as it's against forum policy to tell you

---

### Post by sisco311 on 2009-07-25
please read the link posted by SuperSonic4.

in short, the equivalent of *su -* in Ubuntu is *sudo -i*.

after running the command you are asked for your user password, type it and press Enter. 
there is no visual feedback when you type the password.

---

### Post by kart168 on 2009-07-25
thank you sisco and supersonic. it works for me now

:D

---

### Post by sisco311 on 2009-07-25
> **kart168 said:**
> thank you sisco and supersonic. it works for me now

:D

Cool!

Please be careful while running applications with root privileges as you may damage your system.

Btw, you can *log out* from the root shell with the *exit* command or by pressing Ctrl+d.

EDIT: for a single command simply prepend sudo to it. i.e.:
```
sudo apt-get update
```

---

