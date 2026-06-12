---
title: "Using dd on SSD"
date: 2011-09-21
forum: General Help
---

### Post by Ceiber Boy on 2011-09-21
I've read a lot on and have successfully clones HDD, but what is the situation with using it on SSD, do all the same principles apply or are their some variables or other factors that I need to be aware of?

I ask as I have read that the mechanism for writing to SSD is different to HDD.

Thanks

---

### Post by dcstar on 2011-09-21
> **Ceiber Boy said:**
> I've read a lot on and have successfully clones HDD, but what is the situation with using it on SSD, **do all the same principles apply** or **are their some variables or other factors that I need to be aware of?**


[LIST=1]
[*]Essentially, yes.
[*]Just avoid doing a dd more than once for the same partition without using TRIM tools to release the previously used blocks.
[/LIST]

---

