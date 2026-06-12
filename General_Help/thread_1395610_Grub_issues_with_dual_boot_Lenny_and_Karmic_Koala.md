---
title: "Grub issues with dual boot Lenny and Karmic Koala"
date: 2010-02-01
forum: General Help
---

### Post by ozguitarplayer on 2010-02-01
Hi,
I have a laptop with Karmic Koala in dual boot with Debian Lenny. 
I need to reinstall Lenny, however if I do that I will loose Karmic Koala from the grub screen at startup because of the new version of grub in Karmic Koala.
This means that I would have to reinstall Karmic Koala after I reinstall Lenny in order for them to both appear in the grub screen.
If I reinstall only Lenny is it possible to use Gparted to change the boot back to Karmic Koala and have them both appear again in the grub screen at startup?
Or is there another way to get around the issue?

---

### Post by Leppie on 2010-02-01
both lenny and karmic offer the possibility to skip installtion of the boot loader. however, i believe that karmic requires the alternate cd, so it may be easier installing lenny without boot loader.
it's been a while since i did my lenny install, but if i remember well during the final stage it should offer you the option to just skip installing a boot loader.

---

### Post by ozguitarplayer on 2010-02-01
Thanks, I now remember that there is an option not to install the boot loader. Would this still mean that mean that both operating systems would appear in the grub boot screen?

---

### Post by Leppie on 2010-02-01
> **ozguitarplayer said:**
> Thanks, I now remember that there is an option not to install the boot loader. Would this still mean that mean that both operating systems would appear in the grub boot screen?
well, after having installed lenny without the boot loader boot into ubuntu and rund update-grub to have your newly installed lenny detected.

---

### Post by ozguitarplayer on 2010-02-01
Thanks again, I'll be trying it this morning, I'll let you know how iy went.

---

### Post by ozguitarplayer on 2010-02-01
Done, thanks everyone.
As suggested I choose not to install grub with the Lenny install. Next question asked what partition was to be used for grub and I pointed to the Karmic Koala partition. After installation I booted into Karmic Koala and did #update-grub and that was it.
It's so good working with Linux systems as there seems to always be a way do thinks, and the support is fantastic!
Thanks again.

---

### Post by Leppie on 2010-02-01
you're welcome, glad it's all working properly now.
enjoy linux :)

---

