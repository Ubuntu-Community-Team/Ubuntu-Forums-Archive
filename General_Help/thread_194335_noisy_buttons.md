---
title: "noisy buttons"
date: 2006-06-11
forum: General Help
---

### Post by h.mehdi on 2006-06-11
Hi

I use ati driver auto detected by Dapper but with new default Dapper theme, see noisy buttons... looks like "snow" in the "radio buttons" (those "OK" and "Cancel" buttons) in certain applications.

Can any one help ?

Thanks

---

### Post by twisted_steel on 2006-06-11
Do you know what model ATI card you have?

---

### Post by h.mehdi on 2006-06-11
I paste this from "xorg.conf"

Identifier      "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
Driver          "ati"

and I've attached a sample shot of buttons...

PS: I don't have such problem with Clearlooks

---

### Post by h.mehdi on 2006-06-14
I just added 

```
Option          "RenderAccel"   "false"
```

to Device Section in xorg.conf and buttons look fine now ;)

---

