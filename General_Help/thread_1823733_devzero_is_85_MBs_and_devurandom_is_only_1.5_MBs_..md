---
title: "/dev/zero is 85 MB/s and /dev/urandom is only 1.5 MB/s ... Why?"
date: 2011-08-12
forum: General Help
---

### Post by Keypel on 2011-08-12
dd bs=4M if=/dev/zero of /dev/sdc1 is 85 MB/s 
dd bs=4M if=/dev/urandom of /dev/sdc1 is 1.5 MB/s 

How can I make the dd option urandom go faster? Already using bs=4M

---

### Post by gsgleason on 2011-08-12
Calculating random data is going to be slower that just writing zeros.  It's having to do a lot more processing.

If you want to improve it, upgrade your hardware.

---

### Post by Keypel on 2011-08-12
I see. Thanks.

---

### Post by dcstar on 2011-08-13
> **gsgleason said:**
> Calculating random data is going to be slower that just writing zeros.  It's having to do a lot more processing.

If you want to improve it, upgrade your hardware.

Especially generating a 4mb random number - that size probably slows the whole process rather than leaving it at the default 512b.

---

