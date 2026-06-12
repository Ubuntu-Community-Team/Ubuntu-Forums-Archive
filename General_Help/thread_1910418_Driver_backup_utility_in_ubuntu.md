---
title: "Driver backup utility in ubuntu ??"
date: 2012-01-17
forum: General Help
---

### Post by celsiusat on 2012-01-17
Hi all,

  the following are the driver backup utilities which I have found on the net

    i) Double Driver
   ii) Chilly device driver backup
  iii) Jermar softwares WinDrivers backup
   iv) Fabs Auto backup

unfortunately all these are** meant for windows O.S** , now **[COLOR=Red]my question is there a similar utility for ubuntu ?[/COLOR]**

---

### Post by BC59 on 2012-01-17
Depends for what you need the driver. In Windows you need drivers for everything. In Linux the drivers are incorporated to the kernel. In some cases only may you need additional drivers for the network card. You could use if you like proprietary drivers for the video card. But the whole idea is different.

---

### Post by celsiusat on 2012-09-12
> **BC59 said:**
> Depends for what you need the driver. In Windows you need drivers for everything. In Linux the drivers are incorporated to the kernel. In some cases only may you need additional drivers for the network card. You could use if you like proprietary drivers for the video card. But the whole idea is different.

finally found a solution as follows:-


soln: fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`

---

### Post by Mark Phelps on 2012-09-12
That is listing out packages, not drivers.  Backing up packages is NOT the same as backing up drivers.

---

### Post by nothingspecial on 2012-09-12
> **Mark Phelps said:**
> Backing up packages is NOT the same as backing up packages.

er .......  :p

---

### Post by Mark Phelps on 2012-09-12
> **nothingspecial said:**
> er .......  :p

Thanks for catching the typo .. fixed it.

---

