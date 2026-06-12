---
title: "Synaptic &lt;Logical Operators?&gt;"
date: 2010-04-25
forum: General Help
---

### Post by Gyrra on 2010-04-25
I have searched around and not found anyone else with the same problem I am currently facing in regard to Synaptic:

Logical operators no longer work in either method of search.
I found what I thought was a similar problem other users solved by using terminal to:
"sudo update-apt-xapian-index"
I even forced it to rebuild "sudo update-apt-xapian-index -f" and no success.

I know I have used logical operators in the quick search previously but I don't seem to be having any luck at all anymore.

Example:
a quick search of xserver -dbg (this only show packages with BOTH terms in the name when it previously would list all xserver WITHOUT dbg)
<there IS a space between terms>

I even tried several methods of operators and no luck:
- !! NOT
|| OR
+ && AND

Can anyone else confirm this issue?



Lucid 64bit RC

---

### Post by dcstar on 2010-04-25
> **Gyrra said:**
> I have searched around and not found anyone else with the same problem I am currently facing in regard to Synaptic:

Logical operators no longer work in either method of search.
........
Can anyone else confirm this issue?

Lucid 64bit RC

Quick Search uses "or", normal Search uses "and", this seems to be the way Synaptic is built.

---

