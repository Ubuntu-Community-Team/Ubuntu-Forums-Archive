---
title: "How do I crash this thing?"
date: 2010-07-28
forum: General Help
---

### Post by cheapie on 2010-07-28
Does anybody know how to crash Ubuntu? I'm looking for a kernel panic, not a freeze. It's OK if it doesn't work in Ubuntu as long as it works in Debian.

P.S. I've already tried killing init.

---

### Post by jerenept on 2010-07-28
Are you ok? I mean, why would you want to crash your computer?
Seriously, it is not advisable to do these things

---

### Post by cheapie on 2010-07-28
I was talking about the kind that just need a reboot to fix. I'm running the suggestions in a VM anyway.

---

### Post by iponeverything on 2010-07-28
Exhaust the memory.

---

### Post by cheapie on 2010-07-28
That just froze it.

---

### Post by linux18 on 2010-07-28
I believe 
```

dd if=/dev/urandom of=/dev/mem

```or 
```

while 1 =1; do echo 1 > /proc/* ; echo 1 > /proc/*/* ; echo 1 > /proc/*/*/* ; echo 1 > /proc/*/*/*/* ; echo 1 > /proc/*/*/*/*/* ; done

```will do it

---

