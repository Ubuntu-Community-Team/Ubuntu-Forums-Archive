---
title: "Repository Problems??"
date: 2010-11-24
forum: General Help
---

### Post by tech7 on 2010-11-24
I'm using 10.10 i386 on hp pavilion dv9620us.
The top panel keeps showing a red triangular caution alert that when moused over reads:
"The update information is outdated.  This may be caused by network problems or by a repository that is no longer available.  Please update manually by clicking on this icon and then selecting 'Check for Updates'and check if some of the repositories fail."

I had clicked this button a few times.  The first time it installed a kernel update.  The next couple times I don't think it did anything but check for updates.

Can anybody help me get this resolved please???

---

### Post by sikander3786 on 2010-11-24
Go to Applications > Accessories > Terminal and post the output of

```
sudo apt-get update
```

Remember, we need the complete output. Just copy/paste here and then wrap it using proper code # tags from the post menu. Or type [/code] at the end and [code] at the beginning of it.

Thanks.

---

### Post by tech7 on 2010-12-04
i had to go into software sources and get rid of the ubuntu cd option.  that fixed the prob..  thanks.

---

