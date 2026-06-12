---
title: "Wireless USB Adapter - VirtualBox"
date: 2010-03-01
forum: General Help
---

### Post by altjx on 2010-03-01
Is there a way to pass a USB device such as a Wireless Adapter, to a guest OS in VirtualBox? In the Devices > USB Devices, it shows <none available>. I'm guessing there has to be a way to do this though =\

---

### Post by nereid on 2010-03-01
Depends on the version of the VirtualBox. With the version, which is included in the Ubuntu repositories, it is not possible. You have to get the version from the SUN page, as this will support USB devices. Just search for VirtualBox and USB.

---

### Post by altjx on 2010-03-01
> **nereid said:**
> Depends on the version of the VirtualBox. With the version, which is included in the Ubuntu repositories, it is not possible. You have to get the version from the SUN page, as this will support USB devices. Just search for VirtualBox and USB.

Thanks, gonna give it a shot.

---

### Post by altjx on 2010-03-01
Just downloaded the VirtualBox from the website, added myself to the vboxusers group, still "No available devices"

EDIT: wow, wtf? I went back to check Users and Groups and there's nomore vboxusers group anymore? Wonder what could have happened?

---

### Post by emanuel.b on 2010-03-01
Some wireless USB adapters do not act a normal USB devices. So, you'll have to use shared networking to access the internet from the guest...

---

