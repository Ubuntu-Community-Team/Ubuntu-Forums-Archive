---
title: "Possible to make program start after certain amount of time?"
date: 2012-04-07
forum: General Help
---

### Post by Dgameman1 on 2012-04-07
When I use the startup program, it opens up pidgin right when the computer starts, which would be fine except, I want to make it start about 4 seconds after Ubuntu loads. Would it be possible to do thaT?

---

### Post by papibe on 2012-04-07
Hi Dgameman1.

Instead of calling pidgin directly on 'Startup Applications', you could write a very bare bone script like this:
```
sh -c 'sleep 4; pidgin'
```
That simple script execute 2 instructions: wait for 4 seconds (sleep), and then call pidgin.

I hope that helps.
Regards.

---

