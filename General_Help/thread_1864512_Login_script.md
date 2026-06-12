---
title: "Login script"
date: 2011-10-19
forum: General Help
---

### Post by alco75 on 2011-10-19
What's the right/best place to put a (bash) script that needs to be run during or post login?

Thanks

---

### Post by alco75 on 2011-10-19
Okay well, I've answered my own question.

The easiest way to achieve this is probably to just create an executable bash script and set it as a startup application.

In Xubuntu, that's Settings Manager -> Session and Startup -> Application Autostart -> Add

---

### Post by ulysses768 on 2011-10-19
Session and Startup hasn't been working for me in 11.10.  It seems as though the startup program has changed.


In general I've been told: 

System wide environmental variables and startup programs should go into /etc/profile
System wide aliases and functions should go in /etc/bashrc.  
Personal environment variables and startup programs should go into ~/.profile.  
Personal aliases and functions should go into ~/.bashrc.

---

### Post by alco75 on 2011-10-20
~/.profile

works perfectly, that's all I needed to know, thank you!

---

### Post by zero2xiii on 2011-10-20
> works perfectly, that's all I needed to know, thank you!

Please mark this thread as solved :)

Thread tools > Mark this thread as solved.

Thanks

---

