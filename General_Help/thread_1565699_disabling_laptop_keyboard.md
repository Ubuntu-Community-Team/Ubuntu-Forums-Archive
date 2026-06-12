---
title: "disabling laptop keyboard"
date: 2010-09-01
forum: General Help
---

### Post by katana1000 on 2010-09-01
I have an old laptop whose keyboard I d like to disable and use the usb keyboard instead, because its defective and keys keep getting pressed. 

Upon search I found the solution of adding i8042.nokbd in the kernel bootline. I have edited the file /boot/grub/grub.cfg and added the line i8042.nokbd under the Operating system I am currently using. However , it does not seem to work.

Can anyone point me in the right direction?

---

### Post by 4ebees on 2010-09-01
> **katana1000 said:**
> I have an old laptop whose keyboard I d like to disable and use the usb keyboard instead, because its defective and keys keep getting pressed. 

Upon search I found the solution of adding i8042.nokbd in the kernel bootline. I have edited the file /boot/grub/grub.cfg and added the line i8042.nokbd under the Operating system I am currently using. However , it does not seem to work.

Can anyone point me in the right direction?


This may help:

[http://csincock.customer.netspace.net.au/lock-keyboard-for-baby.htm](http://csincock.customer.netspace.net.au/lock-keyboard-for-baby.htm)

:)

---

