---
title: "Over write ram."
date: 2011-03-07
forum: General Help
---

### Post by robofighter on 2011-03-07
During shutdown, How do I get Ubuntu to overwrite what is in the RAM.

I know this is an unusual question, but I am curious.

---

### Post by JKyleOKC on 2011-03-07
While it would be possible to do what you ask, it would be wasted effort, because the content of modern RAM vanishes within a very few seconds after the power goes off. It's not at all like the old magnetic-core memories used in mainframes of the 1960s, which could retain their data for weeks without power (but could only be read by erasing the data).

Overwriting 4 GB of RAM would add an appreciable delay to the shutdown sequence, and of course not all the RAM could be cleared anyway because as soon as the program and operating systems areas were overwritten the action would stop. Do you have some specific reason for wanting to do this?

---

### Post by robofighter on 2011-03-22
Paranoid security measures.

---

### Post by jerome1232 on 2011-03-22
If someone where to try to get at the contents of your ram I don't believe they'd properly shutdown your computer first. They'd cut power then quickly execute the required steps to get your memory modules and get the data off them. 

Just don't leave the computer running unattended? If someone breaks down your door then cut power to the computer quickly?

---

### Post by deathadder on 2011-03-22
I suppose you could modify the shutdown process so that once all of the services etc have shutdown you could run memtest which writes random values into memory. But like the others have said, once the power has gone the contents of ram will be gone within moments...

For security I would be far more concerned about ensuring my harddrivers were encrypted correctly because unlike ram those are nice and accessible to anyone with access to the machine.

---

