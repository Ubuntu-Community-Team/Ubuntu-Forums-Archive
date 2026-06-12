---
title: "What is the easiest way to know if a laptop has 64-bit hardware?"
date: 2011-12-04
forum: General Help
---

### Post by geek2330 on 2011-12-04
So to install Ubuntu 64-bit.

---

### Post by OrangeCrate on 2011-12-04
Assuming that you're running Windows 7, right click on Computer, and then click on Properties. It'll tell you there, under System Type.

---

### Post by geek2330 on 2011-12-04
No, running Ubuntu 11.04

---

### Post by papibe on 2011-12-04
If the CPU supports it, you are OK.

However, it may be not worthy if you don't have 4Gb+ of RAM.

Just my thoughts.
Regards.

EDIT: so you need to know your CPU and see if supports 64bits OSes.

---

### Post by OrangeCrate on 2011-12-04
<nevermind>

---

### Post by oldos2er on 2011-12-04
> **geek2330 said:**
> So to install Ubuntu 64-bit.

```
cat /proc/cpuinfo
``` look for the "lm" flag.

---

### Post by collisionystm on 2011-12-04
go to your system bios and look at the cpu info. it will say whether it is 64 bit capable or not

---

### Post by idoitprone on 2011-12-04
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

```
grep --color=always -iw lm /proc/cpuinfo
``` basically oldos2er suggestion but this time it has coooolooooooorrrrrrr oooooooooooooooooooooooooooo

---

