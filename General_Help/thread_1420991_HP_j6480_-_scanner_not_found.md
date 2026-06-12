---
title: "HP j6480 - scanner not found"
date: 2010-03-03
forum: General Help
---

### Post by mynot on 2010-03-03
Having spent hours and hours on this, I'm ready to give up on Ubuntu. Whenever I run Xsane or Vuescan, I get a message telling me there are no devices available. 

Op system is Hardy.
HP J6480 is conected to network hub.
Vuescan works fine under Windows 2000. 
Printing works fine from Ubuntu.
I have repeatedly installed HPLIP.
I have run hp-check and loaded all the dependencies it told me it couldn't find, reducing the number of errors from 9 t(mostly compile time) to 3.
Hp-check finds the printer ok, but tells me no scanners were identified.

The silly thing is that before I re-installed Ubuntu I managed, somehow, after a lot of work, to use Xsane.

Thanks
Tony

---

### Post by mynot on 2010-03-05
Installing HPLIP 3.10.2 manually seemed to fix the problem with Xsane.
Tony

---

