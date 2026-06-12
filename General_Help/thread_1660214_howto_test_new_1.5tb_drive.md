---
title: "howto test new 1.5tb drive?"
date: 2011-01-05
forum: General Help
---

### Post by Lampi on 2011-01-05
hello

I bought a new 1.5TB SATA drive (WD15EARS), now I intend to thoroughly test it for bad sectors and other issues, before it will become part of a server raid array.

Are there any good testing tools out there to perform read/write compare operations allover the disk space?

thanks for some inputs!

---

### Post by kidders on 2011-01-06
Hi there,

Assuming your new disk supports SMART, the best (and probably fastest) option would be to run a "long" test on it. Alternatively, you could use badblocks.

I hope that helps.

---

