---
title: "Ubuntu suspending to swap file?"
date: 2011-01-31
forum: General Help
---

### Post by [Snc] on 2011-01-31
I have read somewhere, that Ubuntu can not suspend itself into a swap file, is that true?

---

### Post by vanadium on 2011-01-31
For "hibernate", the contents of RAM are stored into the swap. "Standby" or "Hibernate" may not work, depending on the brand and type of your computer.

---

### Post by [Snc] on 2011-01-31
> **vanadium said:**
> For "hibernate", the contents of RAM are stored into the swap. "Standby" or "Hibernate" may not work, depending on the brand and type of your computer.

Well, they all work, but i wold like to move my swap partition away from my SSD (too precious to me) and make it a swap file on a normal HDD ... If i don't lose hibernation with that, then i'm forced to make another swap partition on a normal HDD.

(my use of swap is ... let me see ... 0.000014 % yearly)

---

### Post by QLee on 2011-01-31
[QUOTE='[Snc]'...
(my use of swap is ... let me see ... 0.000014 % yearly)[/QUOTE]

In that case, its use is not likely to add much to the wear of your SSD and it probably has wear leveling anyway.

---

### Post by [Snc] on 2011-01-31
> **QLee said:**
> In that case, its use is not likely to add much to the wear of your SSD and it probably has wear leveling anyway.

But its 4GB of unused (badly used) disk space ...

---

### Post by wojox on 2011-01-31
How much memory do you have?

---

### Post by [Snc] on 2011-01-31
8gb, but the system sees only 4 (I am using Ubuntu 64bit, but the motherboard bios seems "broken")

PS. Also, when I installed, it seemed to notice just 2Gb, since I didn't know, that dual channel will not work (the mobo thing)

---

