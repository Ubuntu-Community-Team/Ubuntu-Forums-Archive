---
title: "quote of the day"
date: 2010-02-16
forum: General Help
---

### Post by viralmeme on 2010-02-16
What's that bash command that automatically inserted a quote at the end of your email? Can't recall exactly, is floating round at the back of my mind.

---

### Post by bogdan.veringioiu on 2010-02-16
Hi.
"fortune" is the program that is giving smart quotes in the terminal.
However, I do not know about email....
Bogdan

---

### Post by tjoff on 2010-02-16
To mail the quote from the fortune program, do:

fortune | mail -s "fortune of the day" name@domain

where name@domain is your email adress.
You need to have the package mailutils installed.

---

### Post by viralmeme on 2010-02-17
> **tjoff said:**
> To mail the quote from the fortune program, do:

fortune | mail -s "fortune of the day" name@domain

where name@domain is your email adress.
You need to have the package mailutils installed.
Thanks all, now all I need is a big meaningfull quotes file .. :)

---

### Post by rnerwein on 2010-02-17
hi
----> apt-get install fortune-mod

have fun
ciao

---

