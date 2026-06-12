---
title: "Your system encountered a serious kernel error 9.10"
date: 2009-10-31
forum: General Help
---

### Post by bagodonut1 on 2009-10-31
Can someone please help me out? I just did a fresh install of 9.10. Was running 9.04 and it was ok. Now, under 9.10, every time I log in, I get a red ! saying "Your system encountered a serious kernel error" The system seems to run ok, but it can't be good. Anyone know what this is experiencing the same problem?

I fairly new to linux not sure what info I would need to provide here or commands to get that info. so, let me know if you could.

I appreciate any help.

Thank you!!!!

---

### Post by ibuclaw on 2009-10-31
> **bagodonut1 said:**
> Can someone please help me out? I just did a fresh install of 9.10. Was running 9.04 and it was ok. Now, under 9.10, every time I log in, I get a red ! saying "Your system encountered a serious kernel error" The system seems to run ok, but it can't be good. Anyone know what this is experiencing the same problem?

I fairly new to linux not sure what info I would need to provide here or commands to get that info. so, let me know if you could.

I appreciate any help.

Thank you!!!!

Did it happen when you logged in today?

If so, run:

```

dmesg > ~/Desktop/dmesg.log
cat /var/log/messages > ~/Desktop/messages.log
cat /var/log/kern.log > ~/Desktop/messages.log

```
And attach the .log files created to your next post.

Regards
Iain

---

### Post by bagodonut1 on 2009-10-31
Logs attached


Thanks in advance

---

### Post by sloggerkhan on 2009-10-31
It might be this:
[https://bugs.launchpad.net/bugs/422536](https://bugs.launchpad.net/bugs/422536)

hordes of people are getting it.

---

### Post by jmore9 on 2009-10-31
I had some problems early on and figured oot the if i turned off firestarter the kernel errors went away.

---

### Post by ibuclaw on 2009-11-01
> **bagodonut1 said:**
> Logs attached


Thanks in advance

Run a MEMTEST on your system, just to ensure that you haven't got failing/faulty RAM.

Regards
Iain

---

