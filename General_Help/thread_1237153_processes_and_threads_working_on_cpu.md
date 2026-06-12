---
title: "processes and threads working on cpu"
date: 2009-08-11
forum: General Help
---

### Post by delirejisor on 2009-08-11
Hi,

I want to see the processes and threads working on each processor(processor#1 and processor#2 for a dual-core machine) and their cpu and memory usage on a multi-core machine.
"top" does not show that.

How can i do this?

Thanks

---

### Post by P4man on 2009-08-11
actually, top can show that info.

Press "f" to add columns, then toggle the column "last used cpu" by hitting "j" key. Enter to confirm. You now have a colum P which is zero or one for each core.

press h for more help in top.

---

### Post by delirejisor on 2009-08-11
> **P4man said:**
> actually, top can show that info.

Press "f" to add columns, then toggle the column "last used cpu" by hitting "j" key. Enter to confirm. You now have a colum P which is zero or one for each core.

press h for more help in top.

thanks a lot.that really does what i want.

---

