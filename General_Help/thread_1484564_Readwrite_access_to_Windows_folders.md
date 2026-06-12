---
title: "Read/write access to Windows folders"
date: 2010-05-15
forum: General Help
---

### Post by Lynxman on 2010-05-15
I recently installed Ubuntu 10.04 using Wubi on an ACER Aspire 5000 XP laptop. Everything runs ok and I can access my Windows folders from Ubuntu through the host directory but only as Read Only. I have checked to make sure that the Windows folder I want to access (My Documents) is not designated as Read Only in Windows.

Can anyone tell me how to get Read/Write privilege in Ubuntu?

Thanks

---

### Post by Sin@Sin-Sacrifice on 2010-05-15
It's a matter of how it's mounted. Do you have it set to mount at boot in the fstab? If so you have to add the rw option. If not you can remount it ```
sudo mount -o remount,rw /dev/sdx
``` Changing sdx to the windows drive.

---

