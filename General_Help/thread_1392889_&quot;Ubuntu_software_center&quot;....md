---
title: "&quot;Ubuntu software center&quot;...???"
date: 2010-01-28
forum: General Help
---

### Post by robertcoulson on 2010-01-28
Hi....When I try to load "Ubuntu Software Center" it comes on for about a second or two then closes...I am baffled.
Bob

---

### Post by sisco311 on 2010-01-28
Open a terminal (Applications -> Accessories -> Terminal)
run:
```
software-center
```
and post the error message here.

---

### Post by robertcoulson on 2010-01-28
Thank you for your speed..Here is the error message.
Bob

---

### Post by sisco311 on 2010-01-28
> **robertcoulson said:**
> Thank you for your speed..Here is the error message.
Bob

Next time, if you have to, please post the output of the terminal in plain text. Include it between [noparse]```
error here
```[/noparse] tags. Thanks.

It looks like, you are affected by this BUG: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/470564](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/470564)

Removing the frei0r-plugins package should solve your issue.

Open Synaptic Package Manager (System -> Administration) search for the package and remove it, or run the following command in a terminal:
```
sudo apt-get purge frei0r-plugins
```

HTH

---

### Post by robertcoulson on 2010-01-28
Sisco311...Your the best man.....Works great now...Wish I had the knowledge you guys (and girls) have...Thanks again.
Bob

---

