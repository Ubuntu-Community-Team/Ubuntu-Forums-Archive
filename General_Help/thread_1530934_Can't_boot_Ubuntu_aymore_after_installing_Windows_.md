---
title: "Can't boot Ubuntu aymore after installing Windows 7 too"
date: 2010-07-14
forum: General Help
---

### Post by Menelaos on 2010-07-14
Hi folks out there,

hope you can help me with this problem:

I've installed 10.04 LTS on a fresh, new build system. It has one HD where Ubuntu has it's own partion. Everything worked perfectliy.

After that I've installed Windows 7 on that system too (seperate partion). From that point it's impossible to start Ubuntu anymore. Seems that W7 has manipulated the MBR.

I can boot Ubuntu only from a Live CD.

Is it possible to install a dual boot option after that?


Many thanks
Menelaos

---

### Post by philinux on 2010-07-14
> **Menelaos said:**
> Hi folks out there,

hope you can help me with this problem:

I've installed 10.04 LTS on a fresh, new build system. It has one HD where Ubuntu has it's own partion. Everything worked perfectliy.

After that I've installed Windows 7 on that system too (seperate partion). From that point it's impossible to start Ubuntu anymore. Seems that W7 has manipulated the MBR.

I can boot Ubuntu only from a Live CD.

Is it possible to install a dual boot option after that?


Many thanks
Menelaos

Windows ate grub and put it's own stuff in the MBR

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by Menelaos on 2010-07-15
> **philinux said:**
> Windows ate grub and put it's own stuff in the MBR

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)


Excellent, I followed these instructions and now my Ubuntu boots again.:D

But: After starting the system Ubuntu boots immediately. There is no chance to select the start of W7. :(

---

### Post by BigCityCat on 2010-07-15
Try this

[http://ubuntuforums.org/showpost.php?p=8008800&postcount=3](http://ubuntuforums.org/showpost.php?p=8008800&postcount=3)

---

### Post by Menelaos on 2010-07-15
> **BigCityCat said:**
> Try this

[http://ubuntuforums.org/showpost.php?p=8008800&postcount=3](http://ubuntuforums.org/showpost.php?p=8008800&postcount=3)


SOLVED!

A short "update-grub" and everything worked fine.

Thank you philinux and BigCityCat!!!

---

