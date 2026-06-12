---
title: "What does this ati note means and how can i check it"
date: 2010-02-05
forum: General Help
---

### Post by aviramof on 2010-02-05
Note: If a Linux 2.6.11 or newer kernel was built with
CONFIG_AGP enabled, the kernel AGP frontend is required to load
the fglrx kernel module. To identify whether your kernel was built
with CONFIG_AGP enabled, look for CONFIG_AGP=y in the
kernel config file, or if the 'agpgart' module is loaded.

thanks in advance.

---

### Post by cariboo on 2010-02-06
IF you are using 2.6.11, it's time to upgrade your system, Karmic is currently at 2.6.31.

Just ignore the message, as the agpgart module is installed and loaded by default, if an agp graphics card is detected.

---

### Post by aviramof on 2010-02-06
i'm using latest 8.10 kernel which is 2.6.27-17 i don't use latest version because i don't think 9.04 and 9.10 are stable versions in fact i have tried them and i even wasn't able to connect to the internet via pppoeconf so i'm hopping version 10 would be better then
this two versions.

---

