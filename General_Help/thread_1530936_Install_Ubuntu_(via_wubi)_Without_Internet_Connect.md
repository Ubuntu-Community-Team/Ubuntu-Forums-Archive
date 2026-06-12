---
title: "Install Ubuntu (via wubi) Without Internet Connection"
date: 2010-07-14
forum: General Help
---

### Post by WitchBlade on 2010-07-14
any1 pls help me.. i hve a copy of Ubuntu and want to install it into my notebook (windows 7).. i plan to make dual operating system..anyway, i already tried using wubi but it requires an internet connection.. is there any othet way to install it offline?

---

### Post by philinux on 2010-07-14
> **WitchBlade said:**
> any1 pls help me.. i hve a copy of Ubuntu and want to install it into my notebook (windows 7).. i plan to make dual operating system..anyway, i already tried using wubi but it requires an internet connection.. is there any othet way to install it offline?

> From wubi site faq's.


Can I use an existing ISO/CD instead of letting Wubi download a new one?

Yes, physical CDs will be detected automatically, pre-downloaded ISOs should be placed in the same folder as Wubi.exe. Please note tha Wubi 8.10 requires the Desktop 8.10 CD/ISO. The DVD and Altrenate CD/ISO will not work. You can find the 8.10 ISO here. If Wubi does not find an appropriate ISO/CD and/or if the ISO/CD is corrupted, it will automatically download a new ISO. It is recommended to let Wubi download the ISO for you.
.

---

### Post by WitchBlade on 2010-07-14
so its mean, if i use desktop.9.10.. i must use wubi 9.10?

---

### Post by WitchBlade on 2010-07-14
> **WitchBlade said:**
> so its mean, if i use desktop.9.10.. i must use wubi 9.10?

im have a copy of ubuntu 9.10 in my hd.. can i use wubi 10.04?

---

### Post by m4tic on 2010-07-14
A wubi install means you won't get the best out of ubuntu. Install it side by side with windows by a new partition if you have some knowledge. You have to boot from the cd to be able to do this.

---

### Post by WitchBlade on 2010-07-14
> **m4tic said:**
> A wubi install means you won't get the best out of ubuntu. Install it side by side with windows by a new partition if you have some knowledge. You have to boot from the cd to be able to do this.

so i need to burn my copy of ubuntu into a cd and make new partition..?  i know abit about creating new partition

---

### Post by m4tic on 2010-07-14
> **WitchBlade said:**
> so i need to burn my copy of ubuntu into a cd and make new partition..? i know abit about creating new partition
 
Yes you do but it's possible to do on that usb only if your motherboard supports booting from a usb stick. You should change the boot priorities. Remember do everything with caution, from this point on only user error will be to blame if something goes wrong.

---

### Post by WitchBlade on 2010-07-14
> **m4tic said:**
> Yes you do but it's possible to do on that usb only if your motherboard supports booting from a usb stick. You should change the boot priorities. Remember do everything with caution, from this point on only user error will be to blame if something goes wrong.

so, no need use wubi?

---

### Post by sarim on 2010-07-14
> **WitchBlade said:**
> so, no need use wubi?

If you wanna install ubuntu in a new partition wubi is not needed.

If you want to install ubuntu without creating a partition then you can use wubi.

You will always have a wubi inside your ubuntu iso. Just mount the iso using any software like PowerISO. 
then use the wubi inside the iso.

or After mounting you can copy the wubi.exe then paste it in same folder as the ISO. then run the wubi. It will install ubuntu without needing of internet. 
COOL

---

### Post by WitchBlade on 2010-07-14
> **sarim said:**
> If you wanna install ubuntu in a new partition wubi is not needed.

If you want to install ubuntu with creating a partition then you can use wubi.

You will always have a wubi inside your ubuntu iso. Just mount the iso using any software like PowerISO. 
then use the wubi inside the iso.

or After mounting you can copy the wubi.exe then paste it in same folder as the ISO. then run the wubi. It will install ubuntu without needing of internet. 
COOL

thanks.. its works!

i hve tried to connect to wireless internet but i dont know how to setup the wireless connection.. it set it automatically but still cant connect to any wifi here..

---

