---
title: "Uprecords' records gone"
date: 2011-10-06
forum: General Help
---

### Post by Erik1984 on 2011-10-06
I lately experienced a serious freeze (I suspect disk issues) and I had to shut down the computer to reset. Luckily Ubuntu booted fine, filesystem ok and all my data seemed in place. However when I ran uprecords again yesterday the previous records were gone. Now it says: 

```

since                     Tue Oct  4 23:56:00 2011

```In stead of somewhere in August. That time 23:56 is I guess the same time I rebooted the PC after the freeze. How can this happen?

---

### Post by Erik1984 on 2011-10-07
-bump-

---

### Post by CharlesA on 2011-10-07
Not sure if it'll help but I found a [debian bug report]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=536823") about uptimed losing records after a power failure.

---

### Post by Erik1984 on 2011-10-07
> **CharlesA said:**
> Not sure if it'll help but I found a [debian bug report]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=536823") about uptimed losing records after a power failure.

That's something, thanks. Don't know if it contains a fix but certainly worth a read. It's not a big issue anyway but just something that shouldn't happen.

---

