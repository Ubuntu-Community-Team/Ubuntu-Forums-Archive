---
title: "Trim"
date: 2010-11-25
forum: General Help
---

### Post by kentcb on 2010-11-25
All,

The situation with TRIM in Ubuntu has me utterly confused. I don't know whether I need to manually run it or not. Sources I've found are disparate and unclear.

I have Ubuntu 10.04 with latest updates (including kernel 2.6.32-26). I have an Intel X-25M drive with latest firmware, and it is formatted as ext4.

So, does TRIM support run automatically? If not, how do I check if I need to run it, and then how do I run it if necessary?

Thanks

---

### Post by dcstar on 2010-11-26
> **kentcb said:**
> 
.........
So, does TRIM support run automatically? If not, how do I check if I need to run it, and then how do I run it if necessary?

Thanks

[LIST=1]
[*]No. Only 2.6.33+ kernels have it. 10.04 is supposed to have a TRIM enabled kernel one day.....
[*]You run it as often as you need, like when your write performance diminishes.
[*]Search the many posts already explaining how to use it.
[/LIST]

---

