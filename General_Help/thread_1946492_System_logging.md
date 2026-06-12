---
title: "System logging"
date: 2012-03-24
forum: General Help
---

### Post by sideburns on 2012-03-24
My sister's running the latest version of Ubuntu, completely updated.  Earlier today, she was having trouble getting a flashcard mounted and asked me for help.  First, I made sure that it was working OK by mounting it on my laptop.  (Fedora 16)  Then, on her machine I tried to do some trouble-shooting.  In order to watch what, if anythng, happened when I inserted the card, I opened up a terminal and typed this in:

tail -f /var/log/messages

I was quite astonished to be told that the file didn't exist.  Just to make sure, I ran this:

ls /var/log

finding out that not only doesn't it exist, there's no file there that could be considered its replacement.  Apparently, Ubuntu isn't doing any system logging.  Is this normal, and if not, how do I correct it?

---

### Post by wildmanne39 on 2012-03-24
Hi, try this:
```
sudo tail -n100 /var/log/syslog
```
Thanks

---

### Post by sideburns on 2012-03-24
So they've changed messages to syslog.  How quaint.  Alas, -n100 doesn't have the effect I want.  I don't want the last 100 lines, I want to see all new lines as they're entered until I stop it, which is why I specified -f.

---

### Post by wildmanne39 on 2012-03-24
Your welcome!

---

