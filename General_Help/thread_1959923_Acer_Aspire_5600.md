---
title: "Acer Aspire 5600"
date: 2012-04-16
forum: General Help
---

### Post by Amilo1718 on 2012-04-16
Hello all,

Just got an old Acer Aspire 5600 on Ubuntu 12.0 Beta & triggered some nice issues... :p

Sudden shutdown mostly occurs :

1. Playing video using Flash via FF
2. Playing video using Movie player

Shutdown doesn't occur :

1. update manager is working
2. using memtest

all of the above might be a coincidence !?

==> check temperature : 40 degrees Celsius
==> check RAM : no flaws
==> check battery : no battery present (is also not charging but that's another issue - probably)

so... if anyone has some idea of what the heck is going on, please let me know

Grtz

:guitar:

---

### Post by Alexcunn on 2012-04-16
memtest will not check the amount of ram. Are you sure you have enough. It could also be how many processes you are running. You should have at least 1 gb but at 1 gb you should still be careful about your processes.

---

### Post by RJARRRPCGP on 2012-04-16
I dunno. But check the heatsinks for dust.

---

### Post by jadtech on 2012-04-16
sounds like something could be, dirty and over heating ...

---

### Post by Amilo1718 on 2012-04-17
Thanks guys,

Memtest was checking for flawed allocation of bytes on the RAM (2x 512 MB DDR2) but no flaw found

Heating problem : the sensors (3) didn't find anything above 45 degrees so it would be very starnge if it switches of at that temperature :D

Dust :  mmm... could be, will open this thing up & report back later :)

Again guys... thanks

---

### Post by Amilo1718 on 2012-04-17
> **jadtech said:**
> sounds like something could be, dirty and over heating ...

no luck here... after removing 1 particle of dust the laptop still shuts down when using graphical "intensive" applications like flash & movie player...

sensors displayed 42 degrees Celsius at most
swapping RAM didn't help either

Any other ideas?

---

### Post by philinux on 2012-04-17
> **Amilo1718 said:**
> no luck here... after removing 1 particle of dust the laptop still shuts down when using graphical "intensive" applications like flash & movie player...

sensors displayed 42 degrees Celsius at most
swapping RAM didn't help either

Any other ideas?

At login choose the unity 2d session. It sounds like graphics driver/card related.

---

### Post by Amilo1718 on 2012-04-17
> **philinux said:**
> At login choose the unity 2d session. It sounds like graphics driver/card related.

will try now

:popcorn:

would be a pity if that's the reason but maybe that's why it was working on 10.04 LTS without any major issues

---

### Post by Amilo1718 on 2012-04-21
> **philinux said:**
> At login choose the unity 2d session. It sounds like graphics driver/card related.

I removed & add some thermal paste and it worked again as it should be...

Strange but thanks everyone for the help

):P

---

