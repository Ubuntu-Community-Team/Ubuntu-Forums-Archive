---
title: "Is there a way to install 32-bit proprietary printer drivers on a 64-bit system?"
date: 2009-11-23
forum: General Help
---

### Post by jon.reeve on 2009-11-23
I have a Dell printer (v505) which is supposed to work with Linux. Dell provides drivers (proprietary) which work on my laptop (32-bit Karmic) but not my desktop (64-bit Karmic). Are there certain packages I could get that would make these drivers run on 64-bit?

---

### Post by NoaHall on 2009-11-23
Is it in a deb package?
```
sudo dpkg -i --force-architecture /package/location
```

Otherwise, I believe using the cups manager will show the drivers.

---

### Post by jon.reeve on 2009-11-23
Yep, I tried the force-architecture thing before, but it didn't seem to work. Maybe I did something else wrong in the process, though. Are there certain packages I need, like a 32-bit cups?

---

### Post by NoaHall on 2009-11-23
> **jon.reeve said:**
> Yep, I tried the force-architecture thing before, but it didn't seem to work. Maybe I did something else wrong in the process, though. Are there certain packages I need, like a 32-bit cups?

Not, you shouldn't need to. Can you post the output of the error message?

---

