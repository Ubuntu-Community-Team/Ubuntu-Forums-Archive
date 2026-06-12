---
title: "All games lag"
date: 2010-05-31
forum: General Help
---

### Post by fabis94 on 2010-05-31
Since i installed Ubuntu, all of the games i run (at least the 3D ones, like Counter Strike or some Native Linux First Person Shooters) lag.

I have this GFX card - ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

Why is that? Even a native game called Cube 2: Sauerbraten which has almost no sys req lags really much.

---

### Post by WorMzy on 2010-05-31
Have you installed propriety drivers through System -> Administration -> Hardware Drivers?

---

### Post by fabis94 on 2010-05-31
When i open that app, there is nothing there and it just says "No proprietary drivers are in use on this system".

---

### Post by WorMzy on 2010-05-31
In that case you need to download the latest driver from the manufacturer's website (if they offer a Linux compatible driver for it, that is), and install it the old fashioned way, via a terminal.

---

### Post by fabis94 on 2010-05-31
Well okay i did that. I installed the new Catalyst version ati-driver-installer-10-4-x86.x86_64

The thing is after installing it acts like i haven't installed it. Even worse, when i run fglrxinfo i get Segmentation fault. Glxinfo returns 

> name of display: :0.0
Segmentation fault

dmesg | grep err returns:

> [ 2022.043653] fglrxinfo[29868]: segfault at 4 ip 00c72ef6 sp bfa39300 error 4 in libGL.so.1.2[c0d000+a7000]
[ 2024.492046] glxinfo[29869]: segfault at 4 ip 00e8aef6 sp bfeccb00 error 4 in libGL.so.1.2[e25000+a7000]


And when i run aticonfig i get aticonfig: No supported adapters detected

So wtf? Why Ubuntu doesn't want to work with my hardware :(

---

### Post by WorMzy on 2010-05-31
Certainly seems that way. Have you used previous version of Ubuntu/other Linux distros with the same hardware, without any problems? Or is this the first time you've tried Linux on this hardware?

---

### Post by fabis94 on 2010-05-31
This was the first time i'm using Linux on my PC.
Also when i try to run sudo dpkg-reconfigure xserver-xorg nothing happens :/
Like just nothing.

---

### Post by clhsharky on 2010-05-31
fabis94

The RS480 chip is legacy ATI chip, and fglrx does not support it.
The OSS drivers (open source)come by default in Ubuntu for your chip.
Checking at ATI site for recommend driver, for the chip and OS used, will save much pain.

Sharky

---

### Post by fabis94 on 2010-05-31
Well weird, it said the driver supports Radeon Xpress 200G Series.
What should i do now? Uninstall fglrx and install which driver?

Also does this mean that i'm stuck with the drivers that make all the games lag?

---

### Post by clhsharky on 2010-05-31
fabis94

The cat9.3 in ubuntu8.04 is latest supported fglrx, is that what you have?

Sharky

There are newer Radeon drivers.

---

### Post by fabis94 on 2010-05-31
Sorry i'm still pretty new so what exactly is cat9.3?
Also i just uninstalled all the fglrx anyway and installed the open source ones, but i'd still like to find a way to use the proprietary ones.

By the way, when i selected which driver to use, it selected version 9.3 for my driver, but it wouldn't install because apparently my kernel is too new. So i just went ahead and installed the latest version of Ati Catalyst.

Could that have been the problem?

---

### Post by clhsharky on 2010-05-31
fabis94

> By the way, when i selected which driver to use, it selected version 9.3 for my driver, but it wouldn't install because apparently my kernel is too new.

That is why I said Ubuntu8.04, other factors to(xorg).


> So i just went ahead and installed the latest version of Ati Catalyst.
Could that have been the problem?

Yes, the latest version of Ati Catalyst do not support your chip.

If you want to play games with fglrx you need Ubuntu8.04 and Catalyst 9.3.
Fglrx drivers has much better 3D and Power Management compared to OSS drivers ATM. But not liked by many for various reasons(like yours for one).

 Gaming in Wine has never been supported well with ATI as Nv cards are.
TBO  IGP and low power CPU is not ideal for gaming, and can be very frustrating.
Turning off compiz (desktop effects)will take some burden off hardware while gaming.

If your wanting to use Lucid you can install fresher OSS drivers including G3D.

Gaming on your hardware in linux will likley be slow but do'able.

Luck  

Sharky

---

