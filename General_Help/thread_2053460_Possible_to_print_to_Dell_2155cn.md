---
title: "Possible to print to Dell 2155cn?"
date: 2012-09-05
forum: General Help
---

### Post by GammaPoint on 2012-09-05
Hi, I'm running the latest release of Xubuntu at work and my group has a Dell 2155cn laser printer. This printer does not show up when I go to System -> Printing -> Add. Is there another way to get it? I couldn't find drivers for it either. 

Thanks for the help!

Best,
GP

---

### Post by LewisTM on 2012-09-05
[Openprinting]("http://www.openprinting.org/printer/Dell/Dell-2145cn") recommends the  Generic PCL 5c Printer - CUPS+Gutenprint v5.2.5 driver for the related 2145cn. You might have some luck there.

If you want better quality at the cost of speed, you can try the pxlcolor driver which is recommended for the [3100cn]("http://www.openprinting.org/printer/Dell/Dell-3100cn") (my own model).

Sadly, for best graphics (especially photos), nothing beats the Windows driver - at least for the 3000/3100cn. The only workaround then is to print to PDF and bring it to a Windows machine.

Cheers!

---

### Post by GammaPoint on 2012-09-05
> **LewisTM said:**
> [Openprinting]("http://www.openprinting.org/printer/Dell/Dell-2145cn") recommends the  Generic PCL 5c Printer - CUPS+Gutenprint v5.2.5 driver for the related 2145cn. You might have some luck there.

If you want better quality at the cost of speed, you can try the pxlcolor driver which is recommended for the [3100cn]("http://www.openprinting.org/printer/Dell/Dell-3100cn") (my own model).

Sadly, for best graphics (especially photos), nothing beats the Windows driver - at least for the 3000/3100cn. The only workaround then is to print to PDF and bring it to a Windows machine.

Cheers!

Thanks much for the help Lewis. I ended up adding the printer via the IP address and using a generic driver. I was then able to print at quality levels good enough for what I'm doing at least. Thanks again!

---

### Post by gyrene2083 on 2012-09-07
GammaPoint, 

Could you tell me what exactly you used to set up your 2155. I selected the generic driver, as you suggested, but am kind of unsure as to which generic printer I should select.

Thanking you in advance.

-Semper Fi
gyrene2083

Actually belay the last msg. I used the 3000cn Foomatic/pxlcolor driver. I was able to print in colour ok. If you have another driver that works better, please let me know.

---

### Post by GammaPoint on 2012-09-07
> **gyrene2083 said:**
> GammaPoint, 

Could you tell me what exactly you used to set up your 2155. I selected the generic driver, as you suggested, but am kind of unsure as to which generic printer I should select.

Thanking you in advance.

-Semper Fi
gyrene2083

If I look at my printer properties on the newly set up printer it says:

> Generic PCL 6/PCL XL Printer Foomatic/pxlcolor (recommended)

Hope this helps.

---

### Post by gyrene2083 on 2012-09-08
@GammaPoint, I appreciate the help. Thank you.

-Semper Fi
gyrene2083

---

