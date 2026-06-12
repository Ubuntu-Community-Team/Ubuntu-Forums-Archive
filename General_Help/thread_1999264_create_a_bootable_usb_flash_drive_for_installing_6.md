---
title: "create a bootable usb flash drive for installing 64-bit Ubuntu using 32-bit Ubuntu"
date: 2012-06-07
forum: General Help
---

### Post by subjugater on 2012-06-07
I'm using the startup disk creator on my 32-bit machines. I can successfully create a bootable usb flash drive for installing 32-bit 12.04 Ubuntu, but not the 64-bit one. I tried and failed on two Ubuntu machine and both of them are with 32-bit Ubuntu. 

My guess is that a 32-bit machine can only create a bootable usb flash drive for installing 32-bit Ubuntu. Can anyone confirm this and let me know if there is any workaround to create a bootable flash drive for 64-bit Ubuntu using a machine with 32-bit Ubuntu? 

Thx!!!

---

### Post by ExSuSEusr on 2012-06-07
Have you tried UNetbootin yet?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by subjugater on 2012-06-07
> **ExSuSEusr said:**
> Have you tried UNetbootin yet?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Thx, buddy. Never heard about this and I am trying.

---

### Post by papibe on 2012-06-07
> **ExSuSEusr said:**
> UNetbootin

+1

Hi subjugater.

I've done it using UNetbootin . It shouldn't be a problem.

Sometimes it'is a good idea to first wipe the flash drive using gparted (remove all partition, creating a new one, and format it).

Regards.

BTW, UNetbootin is in the Software Center.

---

### Post by subjugater on 2012-06-07
> **papibe said:**
> +1

Hi subjugater.

I've done it using UNetbootin . It shouldn't be a problem.

Sometimes it'is a good idea to first wipe the flash drive using gparted (remove all partition, creating a new one, and format it).

Regards.

BTW, UNetbootin is in the Software Center.

Man, thanks very much for the detail. I've created a bootable flash drive and will be installing using it.

---

