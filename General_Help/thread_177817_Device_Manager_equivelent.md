---
title: "Device Manager equivelent?"
date: 2006-05-16
forum: General Help
---

### Post by René Kabis on 2006-05-16
I have set up Ubuntu on several machines already, but one of the most frustrating things is that it doesn't have the equivelent of Window's Device Manager.

Yes, it has a utility that shows what hardware was installed. However, that utility fails to display that hardware which was seen, but for which a driver was not found. That is, problem hardware that either doesn't work or was not installed properly.

Does anyone know of a utility that can scan and report hardware/driver setups?

---

### Post by bluevoodoo1 on 2006-05-16
What about...

System > Administration > Device Manager  ??

EDIT: Whoops I think you knew about that.

---

### Post by nanotube on 2006-05-17
try using command "lspci" ?

---

### Post by René Kabis on 2006-05-18
Actually, the Windows Device Manager is far more comprehensive than a simple PCI Bus scanner. And that's what I am looking for. A comprehensive utility that will not only list all of the hardware in a computer that *is* working fine, but also all of the hardware that isn't, as well as that hardware for which a driver couldn't even be found. Having a right-click -> "update driver" functionality for each item in the hardware list would also be great, as that would allow a person to custom-tailor the driver to the device via the GUI if the wrong driver was installed.

---

