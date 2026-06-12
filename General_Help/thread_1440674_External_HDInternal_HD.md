---
title: "External HD/Internal HD"
date: 2010-03-27
forum: General Help
---

### Post by jwtownshend on 2010-03-27
Hi!

I installed Ubuntu 10.04 beta 1 on an external Hard drive. During installation I tried getting it to install Grub on the External HD, but instead it put it on my Windows Internal Hard drive. (I think I did something wrong)

Now, I would like my external hard drive to boot with grub on it when it is plugged in before my laptop is turned on.

Is there a way to get grub on the External HD so I can then overwrite the grub on the internal windows HD with the windows boot loader.

Please let me know how to do this.

Thanks,


Jwt

---

### Post by theozzlives on 2010-03-27
> **jwtownshend said:**
> Hi!

I installed Ubuntu 10.04 beta 1 on an external Hard drive. During installation I tried getting it to install Grub on the External HD, but instead it put it on my Windows Internal Hard drive. (I think I did something wrong)

Now, I would like my external hard drive to boot with grub on it when it is plugged in before my laptop is turned on.

Is there a way to get grub on the External HD so I can then overwrite the grub on the internal windows HD with the windows boot loader.

Please let me know how to do this.

Thanks,


Jwt

This may not be the only cure (or the best), but I would restore the MBR and boot sector to Windows. Unplug the HD and install Ubuntu on the USB drive. Then, set the CMOS to boot from USB first.

Your system will look to USB and if no MBR is found, go to the HD. I did it that way with my laptop, and a flash drive and it works great!

---

### Post by jwtownshend on 2010-03-27
Thanks but before I go unplugging my internal hard drive, :)

Does anyone have any other way to do this?

---

