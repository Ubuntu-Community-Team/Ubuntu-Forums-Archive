---
title: "Recuire password to run command"
date: 2010-09-13
forum: General Help
---

### Post by Smart Viking on 2010-09-13
Hey everyone.

I have a shortcut on my desktop linking to my server, it looks like:
```
firefox <server IP>
```What i want it to do, is when i click it it will ask for a password, if the correct password is entered then it will execute, if not it will close. This is not for security and i know it is very easy to bypass, but i don't want it to be so easy for my friends to start sneaking around my server and then don't know how to take it away anyway. 

I tried gksudo, but this run firefox with root privileges, that is not what i want, i want it to run firefox as a normal user, maybe there is some way of using gksudo and running firefox with normal privileges?

Thanks! :)

---

### Post by aeiah on 2010-09-13
why dont you just put a password on your server? :p

you can launch gksu/gksudo as your own user by passing the -u flag, and you can provide a message and prompt with -p and -m 'message', but testing it threw up an error for me. your mileage may vary

```

gksu -p -D 'hi' -u username firefox <server ip>

```

---

