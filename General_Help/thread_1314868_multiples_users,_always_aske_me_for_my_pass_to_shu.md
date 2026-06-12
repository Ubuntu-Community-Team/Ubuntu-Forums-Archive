---
title: "multiples users, always aske me for my pass to shutdown or restart ubuntu 9.10"
date: 2009-11-04
forum: General Help
---

### Post by R1kARD0 on 2009-11-04
Everytime i try to shutdown or restart suddenly appears a window asking me for the pass cuz is say that other user is logging in and is driving me crazy xD. on the web i found other ppl have similar problem and no solution :(. when i clic advance option in the windows say the application that is doing it is this: (org.freedesktop.consolekit.system.restart-multiple-users)

i'm on ubuntu 9.10 64bits :/.
ah, and when i use the "users" command on the terminal it says that are two same sessions started :/ .. but i think that's normal, well the other post on the web say so ...

If anyone can help me. please! XD..

And other unralated thing.... 9.04 booting was faster than 9.10 on my machine and i could change the gdm theme. so the ppl that "improve" the new version of ubuntu... :mad: thank you >_<:lolflag:):P

cheers
rik :D

---

### Post by 00ber n00b on 2009-11-04
What method do you use to time the boot time?

---

### Post by fluffman86 on 2009-11-04
1 mississippi...2 mississippi...

---

### Post by R1kARD0 on 2009-11-05
> **fluffman86 said:**
> 1 mississippi...2 mississippi...
:lolflag:

hahaha, no, i don't like mississippis :D.

that's was a really good one :D:lolflag:

but well, if anyone can help me with the shutdown prompt asking me for a pass please T_T. :D

---

### Post by R1kARD0 on 2009-11-06
so, no one knows how to help me with this, im getting tired of writing my pass everything i shutdown or restart :/
pleeease XD

---

### Post by 8472 on 2009-11-14
I would be interested in some solution for this as well, because it always asks for the password when restarting/shutting down, and it's annoying already.

thx

---

### Post by Shazaam on 2009-11-14
Did you or the person that installed Ubuntu create your user account as a limited account? That could explain the password prompt.

---

### Post by 8472 on 2009-11-14
> **Shazaam said:**
> Did you or the person that installed Ubuntu create your user account as a limited account? That could explain the password prompt.


no, I've installed it, and I'm the first and only user using it.

---

### Post by 8472 on 2009-11-27
still no solution for this bug/feature?
at least some hint would be great.
thx

---

### Post by 8472 on 2009-12-10
solution found at here:
[http://www.uluga.ubuntuforums.org/showthread.php?p=8397604#post8397604](http://www.uluga.ubuntuforums.org/showthread.php?p=8397604#post8397604)
or
[http://www.len.ro/2009/11/karmic-various-tricks/](http://www.len.ro/2009/11/karmic-various-tricks/)

works fine.

---

### Post by cariboo on 2009-12-10
I would check if you are logged into a console or something:, open a terminal and type:

```
who
```

If you are the only person logged in you should get an output that looks like this:

```
who
me     tty7         2009-12-10 10:37 (:0)
me     pts/0        2009-12-10 13:37 (:0.0)
```

Of course substitute your user name for me

---

