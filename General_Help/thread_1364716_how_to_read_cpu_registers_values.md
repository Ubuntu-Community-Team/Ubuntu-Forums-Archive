---
title: "how to read cpu registers values"
date: 2009-12-26
forum: General Help
---

### Post by beyossi on 2009-12-26
Hi all,

how can i read the value of cpu registers?, I guess there is an option doing so through the /proc but don't know exactly how to.
in particular I want to access one of my cpu GPIO (I am using an atom z530).

Thanks.

---

### Post by dcstar on 2009-12-27
> **beyossi said:**
> Hi all,

how can i read the value of cpu registers?, I guess there is an option doing so through the /proc but don't know exactly how to.
in particular I want to access one of my cpu GPIO (I am using an atom z530).

Thanks.

The values in these registers are constantly changing (billions of times a second) so unless you are debugging one particular process (that you can freeze in a debug environment) it seems pointless.

---

