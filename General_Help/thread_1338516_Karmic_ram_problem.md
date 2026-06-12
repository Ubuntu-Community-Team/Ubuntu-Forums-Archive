---
title: "Karmic ram problem"
date: 2009-11-26
forum: General Help
---

### Post by Tomm1 on 2009-11-26
I just found out that my 64bits karmic koala doesn't seem to support 4g of ram.
btw the previous version of ubuntu semms to work with 4g ram.


So i just would like to know  if there is something that i could do to change that.

---

### Post by XCan on 2009-11-26
Do you mean that you're not seeing 4 GB ram or that your computer doesn't boot? What does ```
 uname -a 
``` show? And did you change anything in the bios between the installs, memory remapping comes to mind?

---

### Post by NoaHall on 2009-11-26
It does support 4gb of RAM. I'm using 16, right now. 
Post the output of ```
free -m
```

---

### Post by Tomm1 on 2009-11-26
my computer wont boot at all it just get stuck. but when i remove some of my ram it boots karmic fine

---

### Post by NoaHall on 2009-11-26
> **Tomm1 said:**
> my computer wont boot at all it just get stuck. but when i remove some of my ram it boots karmic fine

Ah, I see. Run memtest.

---

### Post by Tomm1 on 2009-11-27
i runned memtest and it told that there was no errors.
so whats the problem?

---

### Post by NoaHall on 2009-11-27
Hm... Have you changed any hardware at all recently? Does it get passed BIOS?

---

### Post by Tomm1 on 2009-11-27
i just added new ram memory. it gets passed bios. and with 3gigs of ram it boots fine but when i got 4 it just cant boot karmic. in karmic i get some illegal qc-active transition message
btw i cant even install karmic but i tried to instal mint linux 8rc witch is based on karmic  anyway i can install that but it also gets stuck on boot

---

### Post by NoaHall on 2009-11-28
It sounds like to me that your RAM modules are working in slots which don't work properly. I guess you could check for a BIOS update.

---

