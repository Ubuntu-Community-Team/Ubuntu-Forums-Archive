---
title: "Keylogger problem"
date: 2010-09-23
forum: General Help
---

### Post by deviator on 2010-09-23
i was fooling around with lkl and now i cant kill the process

i used```
 ps -eaf | grep -i us_km
``` to search for the process

```
1742  1725  0 07:08 pts/0    00:00:00 grep --color=auto -i us_km
```

and kill it but when i kill -9 it the terminal window just closes.



should i be worried?:mad:

---

### Post by bodhi.zazen on 2010-09-23
What makes you think it is still running after you kill it with kill -9

You probably need to kill it as root and by PID

```
sudo kill -9 PID
```

Change "PID" to the PID #

---

### Post by IcewindDale on 2010-09-23
Hi.

What's getting listed is the *grep* process itself and not us_km. Much in the same way that if you ps -eaf | grep something the following will be presented.


```
5317  3180  0 23:12 pts/0    00:00:00 grep --color=auto something
```

---

### Post by Vigh on 2010-09-23
Keylogger = fail and security/password security risk

Goodluck getting rid of it.

---

### Post by bodhi.zazen on 2010-09-23
> **IcewindDale said:**
> Hi.

What's getting listed is the *grep* process itself and not us_km. Much in the same way that if you ps -eaf | grep something the following will be presented.


```
5317  3180  0 23:12 pts/0    00:00:00 grep --color=auto something
```

Good pickup, I can not believe I missed that !!!

Thank you.

> **Vigh said:**
> Keylogger = fail and security/password security risk

Goodluck getting rid of it.

Although they can be abused and misused, it does not sound as if you are familiar with lkl . It is trivial to install and remove.

---

### Post by Vigh on 2010-09-23
Nah not familar with it, whether its trivial to install or not, its still a security risk for passwords, particularly if someone else has installed it on your computer. I used a keylogger, once! To get my dad password so I could use his computer! lol! Bad move! Got in heaps of trouble.

---

### Post by bodhi.zazen on 2010-09-23
> **Vigh said:**
> Nah not familar with it, whether its trivial to install or not, its still a security risk for passwords, particularly if someone else has installed it on your computer. I used a keylogger, once! To get my dad password so I could use his computer! lol! Bad move! Got in heaps of trouble.

LOL !!!

Keyloggers are not such a big deal in Linux as they are with other OS, but they can be misused.

Most people find them distasteful and their use can be illegal, so be careful ...

---

### Post by deviator on 2010-09-24
> **IcewindDale said:**
> Hi.

What's getting listed is the *grep* process itself and not us_km. Much in the same way that if you ps -eaf | grep something the following will be presented.


```
5317  3180  0 23:12 pts/0    00:00:00 grep --color=auto something
```

good stuff, thanks for that

---

