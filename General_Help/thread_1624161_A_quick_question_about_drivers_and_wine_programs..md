---
title: "A quick question about drivers and wine programs."
date: 2010-11-17
forum: General Help
---

### Post by a quarter past seven on 2010-11-17
i have a few windows programs that Im having trouble recognising my inbuilt microphone, but it works fine with sound recorder and other programs,

and sometimes when i click on audio drivers in winecfg it says there is currently no windows drivers installed or something similar

could my problems with some windows programs in wine be related to the no drivers installed thing,

thanks

Im on a Samsung n130 net-book and running ubuntu net-book remix 10.10 if it makes any difference

---

### Post by Mark Phelps on 2010-11-17
Wine is just a way to run Windows-related services using a Linux OS.  It has nothing whatsoever to do with what drivers are or are not installed.

However, if you run something in Wine (like a 3D game) and it expects to have hardware-accelerated video drivers, it is likely to complain about that if it doesn't find them.

But, since you can NOT install drivers using Wine, you can not fix that problem using Wine, either.

---

### Post by a quarter past seven on 2010-11-17
ok thanks for your answer it cleared things up for me.

---

