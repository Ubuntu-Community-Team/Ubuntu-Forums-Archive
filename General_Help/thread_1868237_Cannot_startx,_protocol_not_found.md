---
title: "Cannot startx, protocol not found"
date: 2011-10-24
forum: General Help
---

### Post by AlecTaylor on 2011-10-24
Good afternoon,

I cannot startx, I get an error "Protocol not found".

(Ubuntu 11.10 x86_64 install was messed up after libjpeg was removed, had to reinstall ubuntu-desktop)

Is there anything I can do to get this working again?

Thanks for all suggestions,

Alec taylor

---

### Post by oldtimer7777 on 2011-10-24
> **AlecTaylor said:**
> Good afternoon,

I cannot startx, I get an error "Protocol not found".

(Ubuntu 11.10 x86_64 install was messed up after libjpeg was removed, had to reinstall ubuntu-desktop)

Is there anything I can do to get this working again?

Thanks for all suggestions,

Alec taylor

Did you install Gnome 3 PPAs on this system and then cause a crash? I have seen this before with Gnome 3 PPA on 11.04.  What do you imagine caused this to happen?

---

### Post by AlecTaylor on 2011-10-24
Nope, I didn't install GNOME from the PPA.

My Xorg.0.log: [http://pastebin.com/XL4GpL9X](http://pastebin.com/XL4GpL9X)
My xorg.conf: [http://pastebin.com/0cQdjvH3](http://pastebin.com/0cQdjvH3)

---

### Post by joelgiedt on 2012-04-30
I have a similar error after installing the Nvidia driver using the install script provided.  I have to do this because the driver that is available the usual way through Ubuntu is too old to be used with CUDA 4.1.  I have to use CUDA 4.1 because the gcc version in Ubuntu 11.04 is too new for older versions of CUDA.  I need to figure out what is wrong with the X configuration and fix it.  I have to use the installed driver.  Thanks.

---

