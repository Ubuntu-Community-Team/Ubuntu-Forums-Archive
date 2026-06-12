---
title: "12GB RAM not all showing"
date: 2010-06-25
forum: General Help
---

### Post by waynemeat on 2010-06-25
Hi folks,

I've 12GB of RAM and its showing as 11.4

Can someone please tell me why this is happing and help me correct this?

I'm running Ubuntu 10.04 x64

Wayne

---

### Post by nmaster on 2010-06-25
the os does things in base 2.  12GB is approximately 11.4 GiB.  everything  is fine.

try looking at the output of "free -b".  that'll tell you the RAM in bytes.

---

### Post by waynemeat on 2010-06-25
> **neal.m.master said:**
> the os does things in base 2.  12GB is approximately 11.4 GiB.  everything  is fine.

try looking at the output of "free -b".  that'll tell you the RAM in bytes.
 
I feel like a right noob now lol. Thank you

---

### Post by nmaster on 2010-06-25
> **waynemeat said:**
> I feel like a right noob now lol. Thank you

no problem.  i was a little disappointed when i saw this thread, since the answer was so trivial, but its no big deal.

---

### Post by dcstar on 2010-06-26
> **neal.m.master said:**
> no problem.  i was a little disappointed when i saw this thread, since the answer was so trivial, but its no big deal.

It won't stop similar posts complaining about the same thing appearing every second day in the forums.

Ubuntu should use either Gib **or **GB consistently in all default output but the mix of both is basically a pain.

---

