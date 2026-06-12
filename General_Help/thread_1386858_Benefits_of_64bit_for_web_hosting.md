---
title: "Benefits of 64bit for web hosting?"
date: 2010-01-21
forum: General Help
---

### Post by Rich78 on 2010-01-21
I'm looking to host some sites with a provider on a Xen VPS running Ubuntu.  It offers both 32bit or 64bit options, so I was wondering what the benefits would be to me if any for hosting my sites?

Sites will be generally Ruby on Rails based.

Thanks.

---

### Post by 3rdalbum on 2010-01-21
Probably extremely minimal benefits for going to 64-bit, except for the greater RAM addressing (unless the 32-bit system has PAE enabled, which it might). More RAM == more cache == faster serving speeds.

---

### Post by howefield on 2010-01-21
> **3rdalbum said:**
> (unless the 32-bit system has PAE enabled, which it might).

It has.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/9.10](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/9.10)

---

### Post by cascade9 on 2010-01-21
If your going to be using ruby on rails with apache, it might be worth going to 64bit- 

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

Apache Benchmark v2.2.11-
32bit- 473 requests per second
32bit PAE- 467 requests per second
64bit- 7989 requests per second (yes, that is 11 short of 8K, not a typo)

---

### Post by Rich78 on 2010-01-24
By god that's a difference in stats!!!  Thanks :D

---

### Post by cascade9 on 2010-01-26
No problem, good luck with your websites ;)

---

