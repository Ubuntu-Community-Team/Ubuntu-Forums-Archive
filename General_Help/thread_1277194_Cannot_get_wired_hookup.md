---
title: "Cannot get wired hookup"
date: 2009-09-28
forum: General Help
---

### Post by oneshot57 on 2009-09-28
I have just installed Ubuntu 8.10 and updated it to 9.04 on 2 laptops and both hook to my wireless router but they will not hook up to wired hookup.I ran the wired hookup in Network manager and after it runs I always get the same thing saying the wired hookup is offline.We tried this in two different houses with the same result.Wireless works,wired does not.....I am new to Ubuntu so please assume you are answering someone who know nothing about Ubuntu beside following the installation CDs instructions.Thanks

---

### Post by P4man on 2009-09-28
Sounds like you got a network card that is not recognized out of the box, and may need drivers. Open a terminal (applications > accessories > terminal) and type

```
lspci
```

copy/paste the output here, so we can see exactly what type of network card you have.

---

### Post by oneshot57 on 2009-09-28
I tried and all I got was command not found

---

### Post by P4man on 2009-09-29
you must have mustyped. copy/paste to avoid typo's. You can paste in a terminal with middle mouse button or shift+control+v
> lspci

lowercase, first letter is an L

---

### Post by Iowan on 2009-09-29
Maybe [this]("http://ubuntuforums.org/showthread.php?t=1156441") one will help - although if wireless works...

---

