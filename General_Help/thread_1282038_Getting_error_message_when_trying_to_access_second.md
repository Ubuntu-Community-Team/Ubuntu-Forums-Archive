---
title: "Getting error message when trying to access second hard drive"
date: 2009-10-03
forum: General Help
---

### Post by pingogo on 2009-10-03
Ht, I installed kubuntu 9.10 beta on my computer.
everything seems to work fine, except when i want to access the second hard drive.
It gives me an error message saying:
org.freedesktop.Hal.Device.Volume.InvalidMountOption The option 'locale=zh_TW.UTF-8' is not allowed for uid=1000

how do i fix this?:confused:
this did not happen to me when i used ubuntu 9.10 beta.

also i can not update softwares in kubuntu 9.10 beta. it says i do not have the necessary privileges to perform this action.

please help me solve these problems. I really like kubuntu interface. 
otherwise i guess i will stick with ubuntu 9.10 beta.

---

### Post by CrusaderAD on 2009-10-03
What's your fstab file look like? Anything out of the ordinary? Try:

> sudo mount -a

See what it tells you.

---

### Post by pingogo on 2009-10-03
i have 3 sata hard drives in my computer.
first hard drive connecting to sata0 is where i installed kubuntu 9.10 beta.
the other 2 hard drives were accessible under ubuntu 9.10 beta but gave me error under kubuntu 9.10.

:confused:

---

### Post by CrusaderAD on 2009-10-04
What's the error?

---

