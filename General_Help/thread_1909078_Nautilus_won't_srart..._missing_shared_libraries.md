---
title: "Nautilus won't srart... missing shared libraries"
date: 2012-01-14
forum: General Help
---

### Post by apochry on 2012-01-14
Hi guys,

today I decided to try Unity 5 and when downgrading back to the stable version I ended up with no Unity at all.
Than I reinstalled the gnome-desktop and now everything else but Nautilus looks fine. It won't start because of the following error:
> ~$ nautilus
nautilus: error while loading shared libraries: libEGL.so.1: cannot open shared object file: No such file or directory
I guess some shared libraries are gone with the uninstalling of Unity...
Reinstalling Nautilus doesn't help.

Any suggestions what could fix this?

System Info:
Ubuntu 11.10 - 32bit
nVidia Video
Intell Processor


Regards,
Christo

---

### Post by TeoBigusGeekus on 2012-01-14
Fire up synaptic and do a search for libEGL. If you find it, just install it and see how nautilus behaves afterwards.

---

### Post by bluexrider on 2012-01-14
if that doesn't work you may want to purge nautilus and reinstall

---

### Post by apochry on 2012-01-15
Thanks for the tips guys,

I fixed the missing libEGL by installing the libegl1-mesa package in synaptic, than another was missing and managed to come around that by downloading and copying the particular file to usr/lib.
Now I'm struck with third **** missing "libpng14.so.14", which is not in synaptic. It is provided with the "libpng14-1.4.8-6.1.src.rpm" package. I tried to download and install it, everything went ok but I still get the same error:
> ~$ nautilus
nautilus: error while loading shared libraries: libpng14.so.14: cannot open shared object file: No such file or directory

I doubt that purging and installing nautilus will do anything.

Do you think that it makes any sense to copy the whole content in usr/lib from a working machine or live cd to my machine? 

Thanks one more time for the help!


Christo

---

