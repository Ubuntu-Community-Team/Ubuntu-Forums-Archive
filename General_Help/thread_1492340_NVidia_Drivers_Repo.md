---
title: "NVidia Drivers? Repo?"
date: 2010-05-24
forum: General Help
---

### Post by PerfectReign on 2010-05-24
How do I tell if I have the NVidia drivers loaded?  I am running 9.1 on a laptop - Compaq nw9440 - with an NVidia Quadro FX 1500m with 256MB RAM.  

I was trying to run Google Earth and it told my my OpenGL VGA card wouldn't handle the 3d graphics well.

I looked and found a few NVidia listings in Synaptic.

I also did an lspci and see NVidia.

> kai@kai-laptop:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation G71 [Quadro FX 1500M] (rev a1)
I looked here: [http://www.ubuntugeek.com/how-to-install-nvidia-drivers-in-ubuntu-feisty-or-later-versions.html](http://www.ubuntugeek.com/how-to-install-nvidia-drivers-in-ubuntu-feisty-or-later-versions.html)

and here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

but don't see anything that tells me to add resositories or auto update NVidia drivers.  I think I did that prior in 9.04. 

(I had recently upgraded from 9.1 to 10.04 but was having too many screen freeze issues so reverted back (fresh install) to 9.1 in order to work.)

---

### Post by v1ad on 2010-05-24
go to System> Adminstration > hardware Drivers. it will search for available drivers and then you should enable the restricted driver.

---

### Post by PerfectReign on 2010-05-24
Thank you!
 
I see it and will be enableing the 185 version.
 
[IMG]http://www.perfectreign.com/stuff/2010/nvidia.png[/IMG]

---

