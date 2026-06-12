---
title: "Battery Netbook Aspire One 532h"
date: 2010-10-19
forum: General Help
---

### Post by mairex on 2010-10-19
Hi there,
I've been using Ubuntu-Netbook (version 10.04) on an ACER Aspire One 532h and the software can not manage the battery properly. Even with the battery half charged it accuses "low battery" and hibernate the system. Sometimes it brings the system for a terminal screen and ask for low graphic mode, where it get stuck. 
Does anyone have any tip?

---

### Post by chessnerd on 2010-10-19
Well, you could disable setting completely, then you just need to make sure that you shut down or hibernate before the computer actually does power off from lack of battery power.

To disable this feature, open up the Gnome Configuration Editor (Alt-F2, gconf-editor) and then go to Apps>gnome-power-management>actions.

Set "critical battery" and "critical ups" to "nothing" (without quotes) and then it shouldn't do that anymore.

---

### Post by mairex on 2010-10-20
> **chessnerd said:**
> Well, you could disable setting completely, then you just need to make sure that you shut down or hibernate before the computer actually does power off from lack of battery power.

To disable this feature, open up the Gnome Configuration Editor (Alt-F2, gconf-editor) and then go to Apps>gnome-power-management>actions.

Set "critical battery" and "critical ups" to "nothing" (without quotes) and then it shouldn't do that anymore.

Hi, chessnerd. Thank you so much. The netbook showed no problem so far!

---

### Post by exchaoordo on 2010-10-25
I've been having this problem for months now and that's the first fix I've heard of.  I wonder if Ubuntu will fix it for real.  On other forums I've seen people suggesting updating the BIOS but that doesn't make much sense to me as I have windows 7 on this machine too and it seems to work fine.

 Thanks for the help, here's hoping it works.:)

---

