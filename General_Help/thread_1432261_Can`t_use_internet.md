---
title: "Can`t use internet"
date: 2010-03-17
forum: General Help
---

### Post by Labus on 2010-03-17
I´m connected to my wireless network but I can´t use internet. Firefox starts but won´t load any pages, evolution doesn´t work either. And I can use internet on my other computers.
I did run computer janitor before this happened, it might have something to do with it.

---

### Post by miniyak on 2010-03-17
i would pop a live cd in to if the web works there.

ive heard a few negative things about the janitor maybe it borked your wireless

Using live cd you can rule out a hardware issue

---

### Post by Labus on 2010-03-17
Internet doesn´t work on a live cd either.
Can the problem be anything else than a hardware issue?
If not,what should I do?

---

### Post by miniyak on 2010-03-17
I hate to ask this because its something simple, but are you sure the card is on?

The next step would be to post the hardware you have, particularly the wireless card.

---

### Post by Iowan on 2010-03-17
Does machine have an IP address? (**ifconfig -a**) If so, can it ping router/gateway? Can it ping internet by name (google.com) or IP address (74.125.95.103)?

---

### Post by miniyak on 2010-03-17
Iowan means open the terminal then type in (or copy and paste)

```
ifconfig -a
```

then try 

```
ping google.com
```

sorry, i myself am sort of unfamiliar with bash. its the type of thing i think should alway be layman's terms

---

### Post by Labus on 2010-03-18
Thanks for all the help but I got it to work, I changed the USB port in wich my antenna was plugged in. When I change it back it still dont work so it's something wrong with that port, but I have 3 more so that's realy not a problem, just interesting.

Either way, Thank you for the help! :D

---

### Post by Dayofswords on 2010-03-18
dont forget to mark as solved(a reply option i beileve)

---

### Post by Labus on 2010-03-18
Done

---

