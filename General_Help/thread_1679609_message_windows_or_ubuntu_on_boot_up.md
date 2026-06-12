---
title: "message windows or ubuntu on boot up"
date: 2011-02-01
forum: General Help
---

### Post by chask on 2011-02-01
I installed a dual system of ubuntu 9.10 desktop a while ago then later uninstalled it. However I still get the message on boot up asking me to choose OS's. It has even survived an HD reformat. 
How do I get rid of it?
Please   Ta
Chask

---

### Post by lanzi on 2011-02-01
Tried typing ```
sudo update-grub
``` on your current installation?

---

### Post by chask on 2011-02-01
Nope, where would I type that? in DOS?
Thanks

---

### Post by tam2tam on 2011-02-01
When you install ubuntu you overwrite the windows loader. This is on the hard disks MASTER BOOT RECORD. There are a number of ways to re-install the bootloader for windows. Google is your friend. CAUTION. You coud inadvertently make your system inoperable. In other words if what you try fails the BIOS may not see a kernel to boot from...ubuntu or windows...so you if in doubt then leave things as they are.

---

### Post by chask on 2011-02-02
As the computer is a new one I put together with bits from Amazon and I used an old hard disk, that looks as though it could be quite fun to try. The worst that could happen is I have to buy a new HD (upgrade from ide to sata at the same time) and reinstall windows (or should it be ubuntu?)
thanks tam2tam
PS love the nickname, was it inspired by the old vaudeville comics? Wish mine was as original.
 
> **tam2tam said:**
> When you install ubuntu you overwrite the windows loader. This is on the hard disks MASTER BOOT RECORD. There are a number of ways to re-install the bootloader for windows. Google is your friend. CAUTION. You coud inadvertently make your system inoperable. In other words if what you try fails the BIOS may not see a kernel to boot from...ubuntu or windows...so you if in doubt then leave things as they are.

---

### Post by Quackers on 2011-02-02
If you only have Windows on your pc now, you need to repair the mbr with the Windows repair disc. Is it Windows Vista or 7? Or do you have XP?
The repair method is slightly different.

---

### Post by lanzi on 2011-02-02
> **chask said:**
> Nope, where would I type that? in DOS?
Thanks

Sorry, I thought you installed different Linux distros. Well if you want the Windows loader just boot from the installation disk and find the startup repair option - should be easy to find on any Win version. The rest will be done automatically ;)

---

