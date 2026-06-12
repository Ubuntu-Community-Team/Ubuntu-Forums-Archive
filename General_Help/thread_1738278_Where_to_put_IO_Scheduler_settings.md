---
title: "Where to put IO Scheduler settings?"
date: 2011-04-24
forum: General Help
---

### Post by Dogers on 2011-04-24
I recently got an SSD and want to switch to using the noop IO scheduler permanently. I understand how to change the scheduler at runtime, but where can I put the command to make it apply on bootup?

I know you can pass "elevator=noop" to the kernel, but that sets all the drives to that scheduler, which I don't want as I still have ye olde spinning drives too - I just want a single drive set to noop..

I'm guessing there's an init script somewhere which is ideal for this, but I've no clue which! Any ideas?

---

### Post by Dogers on 2011-05-08
Okay, found it - /etc/rc.local seems to be the best place

---

### Post by Helkaluin on 2011-05-08
A more proper way is using the /etc/sysfs.conf and the sysfs package.

---

### Post by Dogers on 2011-05-08
Yeah, just come across that one too, although I now have bigger problems since upgrading to Natty :(

---

