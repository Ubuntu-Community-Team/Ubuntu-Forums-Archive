---
title: "Video Drivers"
date: 2010-07-09
forum: General Help
---

### Post by AJH101 on 2010-07-09
I love Ubuntu and have recently installed 10.04 onto a Lenovo lap top. I have installed Regnum Online but am being told my video card is not supported. Can anyone help walk me through updating the driver please?

Thank you

Andrew

---

### Post by Mark Phelps on 2010-07-09
> **AJH101 said:**
> I love Ubuntu and have recently installed 10.04 onto a Lenovo lap top. I have installed Regnum Online but am being told my video card is not supported. Can anyone help walk me through updating the driver please?

Thank you

Andrew

Drivers are specific to the video chip present on the laptop.

To find out what chip you have, open a terminal and enter the following "lspci | grep VGA".

That's a vertical bar between lspci and grep.

Once we know what chip you have, we can provide further details.

---

### Post by AJH101 on 2010-07-09
Hi - does this tell us anything useful?! Thanks!

VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

