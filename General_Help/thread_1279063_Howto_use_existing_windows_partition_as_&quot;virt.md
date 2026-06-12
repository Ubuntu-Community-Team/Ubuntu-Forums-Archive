---
title: "Howto use existing windows partition as &quot;virtual image&quot; with Vbox???"
date: 2009-09-30
forum: General Help
---

### Post by Sp00nman420 on 2009-09-30
Hi All


Im a bit of a n00b to Ubuntu and linux in general. Can someone tell me if it is possible to boot up an existing windows 7 partition in ubuntu using sun virtualbox ??

And if u can how:confused::confused:


Thanks

---

### Post by quixote on 2009-10-01
There was a question like this about a month ago, and I remember somebody answered saying that, yes, that was now possible.  There was a link.  It'll take me a while to find that thread again, but don't lose hope.  There is an answer out there somewhere.

Using an existing Win install under vbox is not equivalent to installing it purely as a virtual machine.  Should both Win itself and the virtual machine try to write to the same file at the same time, very Bad Things happen.  That's why it's usually considered a better idea not to do this unless you really have to.  Just thought I'd mention that in case you weren't aware of it.

---

