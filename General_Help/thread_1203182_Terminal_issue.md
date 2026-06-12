---
title: "Terminal issue"
date: 2009-07-03
forum: General Help
---

### Post by agavril on 2009-07-03
Hi there, for some reason i come home get on my computer and i see terminal open with the command telnet written in.... what is this?

TIA,
  Arthur

---

### Post by Darkspark on 2009-07-03
Telnet is an old program used to remotely connect to another computer. It sounds like you some how had the program running. It's odd that it popped up on your screen like that, especially since it sounds like the telnet client. Is it being started by a process in the background during startup?

---

### Post by agavril on 2009-07-03
no it just once this happened, and ubuntu is feeling kind of sluggish lately

---

### Post by Darkspark on 2009-07-04
You could run the following code and look for what process is starting telnet:
```
ps -ejH
```
and look for telnet.

Also, does this happen ever time you log on?

---

### Post by QIII on 2009-07-04
Do you live with someone who may use a fairly dinosaur-ish method for communicating to a computer at a university for some reason?

---

### Post by agavril on 2009-07-04
> **Darkspark said:**
> You could run the following code and look for what process is starting telnet:
```
ps -ejH
```and look for telnet.

Also, does this happen ever time you log on?
  no this doesnt happen each time i log in, and i checked it only happened once.... but still i am confused.:lolflag:

---

### Post by agavril on 2009-07-04
> **QIII said:**
> Do you live with someone who may use a fairly dinosaur-ish method for communicating to a computer at a university for some reason?
well my dad doesnt no **** about Linux and ubuntu, lol he works with microsoft, so maybe hes trying to use telnet to like start a logging prog. to monitor every thing i do? :P

just a thought.

---

### Post by t4thfavor on 2009-07-04
It was him, he was playing around, and telnet is something he would know how to do.

Thats funny, a logging prog. There are enough noobs on the forum that can't even spell that, and your dad who "doesn't know ****" is going to do that.

Laughable.

Good that we got that cleared up:)

---

### Post by agavril on 2009-07-04
lol hes always trying ways to find out what i am doing, :P beacuse one time i forgot to lock my comp :P so i was suspecting it was him :P

---

