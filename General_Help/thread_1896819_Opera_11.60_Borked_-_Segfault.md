---
title: "Opera 11.60 Borked - Segfault"
date: 2011-12-17
forum: General Help
---

### Post by whatthefunk on 2011-12-17
Anyone else having massive troubles with Opera 11.60?

From the logs:
```
Dec 18 09:38:48 laptop kernel: [  394.155979] opera[1846]: segfault at b6df6fb0 ip 0813418b sp bfbb21d0 error 7 in opera[8048
000+1120000]
Dec 18 09:39:06 laptop kernel: [  412.642779] opera[1861]: segfault at b6e56fb0 ip 0813418b sp bfbae7e0 error 7 in opera[8048
000+1120000]
Dec 18 10:06:20 laptop kernel: [ 2046.052300] opera[2684]: segfault at b6e96fb0 ip 0813418b sp bf91b430 error 7 in opera[8048
000+1120000]

```

Ive reverted to 11.52 and filed a bug report so I guess Ill just have to wait for it to get fixed...

---

### Post by Frogs Hair on 2011-12-17
No problems with either release on 11.10 .

---

### Post by whatthefunk on 2011-12-17
> **Frogs Hair said:**
> No problems with either release on 11.10 .

Thats weird.  Im running Lubuntu 11.10.  The problem started as soon as I updated.  I restarted the computer a couple times with no effect.  Then, I purged opera and installed 11.60 fresh.  Same problem.  I reverted back to 11.52 and everything is fine.

---

