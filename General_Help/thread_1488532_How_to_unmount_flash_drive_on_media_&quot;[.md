---
title: "How to unmount flash drive on /media/_&quot;["
date: 2010-05-20
forum: General Help
---

### Post by potatan on 2010-05-20
Hi,

I think my 4GB Cruzer flash drive has got a bit corrupted as it suddenly has started mounting at /_"[ instead of something along the lines of /45C1-8FE6 (can't remember the actual number).  See the gparted screenshot attached.

So I thought I'd delete the partition, reformat and relabel... but gparted won't let me do it.  When it tries to unmount, I get an error message:
```
sh: Syntax error: Unterminated quoted string
```

*time passes*

Actually, I just figured it out whilst writing this.  I used a umount command in terminal with escape characters, specifically:

```
umount /media/_\"[ 
```

That unmounted it so that I could reformat and relabel.

Thanks for all your help :D

(Will post anyway in case anyone else has a similar problem at some point - including me).

---

### Post by ronnielsen1 on 2010-05-20
> Thanks for all your help :grin:

Not a problem. It's almost like I didn't do anything

---

