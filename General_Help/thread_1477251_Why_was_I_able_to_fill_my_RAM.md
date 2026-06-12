---
title: "Why was I able to fill my RAM?"
date: 2010-05-08
forum: General Help
---

### Post by Zilioum on 2010-05-08
I was programming something for university in c++, using eclipse. At some point I forgot a return statement, which lead to an infinite loop. I didn't stop the program and started to look for the bug. To my surprise my pc started to lag since my little program had filled all my RAM up. 
Isn't memory management supposed to prevent something like this? I did a quick search on the web, about memory management in ubuntu, but didn't really find anything good. I found a lot about caching, but I would also like to know how the available space is distributed? 
Does anyone have some material on that? Material about ubuntu on  a higher level would also be very appreciated (Tutorials tell me "how", but I would also like to know "why").

Cheers

---

### Post by lisati on 2010-05-08
> **Zilioum said:**
> I was programming something for university in c++, using eclipse. At some point I forgot a return statement, which lead to an infinite loop. I didn't stop the program and started to look for the bug. To my surprise my pc started to lag since my little program had filled all my RAM up. 
**[COLOR="Red"]Isn't memory management supposed to prevent something like this?[/COLOR]** I did a quick search on the web, about memory management in ubuntu, but didn't really find anything good. I found a lot about caching, but I would also like to know how the available space is distributed? 
Does anyone have some material on that? Material about ubuntu on  a higher level would also be very appreciated (Tutorials tell me "how", but I would also like to know "why").

Cheers
Well, yes and no. You are right in that part of the job of the memory management system is to try to allocate memory management in a fair and equitable manner to all processes that might need some. One of the challenges faced by designers of memory management systems is that sometimes it has no easy way of telling the difference between a legitimate request for memory, and one made by a program where something has gone wrong.

---

### Post by Zilioum on 2010-05-08
I did play around with this a bit, and I found out that this has nothing to do with eclipse. I get the same result if I run the program from the command line. I did monitor my ram usage while running the program, and it didnt grow steadily. It dropped about 20% at some points, only to go higher up afterwards. It also hits one of the cpus to 100%.
> One of the challenges faced by designers of memory management systems is that sometimes it has no easy way of telling the difference between a legitimate request for memory, and one made by a program where something has gone wrong.
Why?
Is there any further documentation on this topic? Or where could I start looking?

Cheers

---

### Post by Zilioum on 2010-05-12
Ok, maybe I have to rephrase my question: Where would an ubuntu developer start to look if she or he needed a documentation on memory management?

Cheers

---

