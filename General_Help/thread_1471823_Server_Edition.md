---
title: "Server Edition"
date: 2010-05-03
forum: General Help
---

### Post by almangkok on 2010-05-03
I am about to download the Server Edition. How do I know which edition (32 or 64 bits) is suitable for me?

TIA.

--
al

---

### Post by lisati on 2010-05-04
Most recently manufactured computers can run the 64-bit version. You might not notice any significant difference, however, unless you have more than approx. 3Gb RAM.

---

### Post by Leppie on 2010-05-04
to check if you're system is 64 bit, you could run the following command:
```
lshw -c cpu -c display
```
check that both sections contain the line:
```
width: 64 bits
```

---

