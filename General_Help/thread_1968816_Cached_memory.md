---
title: "Cached memory?"
date: 2012-04-29
forum: General Help
---

### Post by llakais on 2012-04-29
Hello,

A system load indicator applet that I installed shows me memory usage. It divides usage up into several categories, one of which is "cache." Is this data that is cached from the hard drive? What does this represent, exactly?

Thanks very much for any help!

---

### Post by cryptotheslow on 2012-04-29
Yes it is data cached from the hard drive to try to improve application performance. The memory is still available for use by applications should they need it.

There's a good explanation here:
[http://www.linuxatemyram.com](http://www.linuxatemyram.com)

---

### Post by codemaniac on 2012-04-29
>              total       used       free     shared    buffers     cached
Mem:           237        200         37          0          6        146
-/+ buffers/cache:         47        189
Swap:          511          8        503
when you run free -m/g or whatever , under -/+ buffers/cache: and free column you can see the actual memory that is free and available to applications to be consumed .
In the above snapshot 47 megs is the amount of memory actually used by the system and free memory is 189 megs which your upcoming applications can use .

---

### Post by llakais on 2012-04-29
Perfect, thanks very much!

---

