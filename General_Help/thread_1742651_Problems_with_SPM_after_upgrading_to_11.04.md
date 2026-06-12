---
title: "Problems with SPM after upgrading to 11.04"
date: 2011-04-29
forum: General Help
---

### Post by hunterkasy on 2011-04-29
I like to remove the not installed (residual config) files so I go into Synaptic package manager and select all of the files I want to remove and click for a complete removal after it gets done doing whatever it does to get them ready, the files are highlighted like they suppose to be, but the apply button on the top is greyed out, so I am unable to remove any files from SPM.  I don't know if this is a bug or just me  could someone help me out?

---

### Post by hunterkasy on 2011-04-30
is anyone else having the same problem or is it just me?

---

### Post by 5149.5 on 2011-04-30
I've seen the same thing. It's not just you.

---

### Post by spiceisland on 2011-05-01
It's a known problem, there is a bug report on it for Ubuntu somewhere (I don't have the link to hand here).

Basically, after having selected and marked-for-complete-deletion the "residual config" items, you also need to mark-for-complete-deletion something else. THEN the apply button becomes clickable.

So, I installed something simple JUST to do this. I chose the 'aft' package (which did not have any dependencies to also install).

Then I marked it for complete-deletion. Then I marked the rest of the residual-config items too. Then hit apply and voila!

---- edit ----

Found the bug report:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/754297](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/754297)

---

