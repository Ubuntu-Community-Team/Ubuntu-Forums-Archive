---
title: "DES_fcrypt()"
date: 2009-10-18
forum: General Help
---

### Post by Bu7753x on 2009-10-18
```
checking if build is possible... configure: error: openssl DES_fcrypt() not found

```

Got this while compiling a encryption program.  How would I get that working?

---

### Post by P4man on 2009-10-19
do you have openssl installed?

---

### Post by Kotfluegel on 2010-08-12
I've got the same problem. Yes, I've already installed openssl via the ubuntu packet manager. But this error still occurs. I'm using ubuntu 9.04 btw.

---

### Post by Bu7753x on 2010-08-16
I recently switched back to Ubuntu (this time on my laptop), and I had the issue again.  It turns out I needed libssl-dev installed on top of openssl.

I was using 9.04 at the time, I'm using 10.10 now.

Ubuntu needs to get it's **** together with fcrypt.

---

