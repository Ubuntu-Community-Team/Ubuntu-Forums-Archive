---
title: "100% compatible video card"
date: 2010-10-22
forum: General Help
---

### Post by ken1mod on 2010-10-22
Gentlemen,

Just installed 10.10 and I am very impressed.

I am not having a big problem at all but my built in video system is clearly behaving like it does not have the right driver.

Are there any video cards out there that are directly well-supported by linux?  i.e. genuine linux drivers that allow the card to function at full capacity or close?

Any thoughts will be appreciated.

Ken

---

### Post by dcstar on 2010-10-22
> **ken1mod said:**
> Gentlemen,

Just installed 10.10 and I am very impressed.

I am not having a big problem at all but my built in video system is clearly behaving like it does not have the right driver.

Are there any video cards out there that are directly well-supported by linux?  i.e. genuine linux drivers that allow the card to function at full capacity or close?

Any thoughts will be appreciated.

Ken

As many other previous threads have already stated, Nvidia & ATI.

---

### Post by efflandt on 2010-10-22
Somebody kept suggesting nVidia GT 220 or GT 240 before.  So when I got a new PC I got one with GT 220.  It does work with default nouveau driver, but not 3D or special effects.

With nvidia activated in System > Administration > Additional Drivers of 10.10 (from beta through release) or Hardware Drivers in 10.04 it has worked great (hardware 3D and much faster than default nouveau driver).  The nvidia drivers are proprietary, but the versions in the Ubuntu repositories have worked fine for me.  Although, people with GTX cards seemed to have issues.

One person with GT 220 that seemed to be overheating must have had a fan issue, because his always showed fan: 0%, and mine stayed much cooler with fan automatically running 30% while testing GPU at 99% until temperature stopped rising.

---

### Post by Bradtek on 2010-10-22
I Have a (from lspci output)
"nVidia Corporation G92 [GeForce GTS 250] (rev a2)"
Restricted Drivers activated.
I have had no issues at all so far with this card 
from 9.04 to 10.10

---

