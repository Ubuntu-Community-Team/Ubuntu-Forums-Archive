---
title: "Figuring out why system crashes randomly via log messages?"
date: 2010-08-29
forum: General Help
---

### Post by James78 on 2010-08-29
Quick question here. My system crashes randomly and (in)frequently, and there's really never a reason as to why it does this, but I'm curious as to why, as it must be a bad problem to be doing this (honestly, my bets are on slightly faulty hardware though).

So, if your system crashed, would whatever happened before that be logged, and where would it most likely be, and how could I view it? I realize it's a simple (sorta stupid) question that I probably know the answer too, but I don't want to waste my time looking for hours if someone here already knows and I can save that time by asking.

Any ideas on how to figure this out?

---

### Post by Rubi1200 on 2010-08-29
System > Administration > Log File Viewer > dmesg

or

Applications > Accessories > Terminal

```
dmesg | less 
```

you could also grep for terms that you think may be related to the problem.

e.g. ```
dmesg | grep <search term>
```

---

### Post by James78 on 2010-08-29
Ah, thanks. Yup, I was right, I already knew, but this provides confirmation for me. :D

---

