---
title: "Startup"
date: 2009-09-06
forum: General Help
---

### Post by dave collin on 2009-09-06
Hi,
A quick one.
How do I change startup so that it skips the listing of kernels/recovery modes and boots directly into the latest kernal (top of the list)?
Thanks
Dave

---

### Post by chriskin on 2009-09-06
> **dave collin said:**
> Hi,
A quick one.
How do I change startup so that it skips the listing of kernels/recovery modes and boots directly into the latest kernal (top of the list)?
Thanks
Dave

either delete them manually through sudo gedit /boot/grub/menu.lst or use the start-up manager application that can be found at synaptic

---

### Post by scouser73 on 2009-09-06
Here is a tutorial for removing old kernels from the Grub menu: [[COLOR="Red"]**Removing Old Kernels**[/COLOR]]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

---

### Post by drs305 on 2009-09-06
Your safest solution is to use StartUp-Manager, a gui app that allows you to tweak a lot of grub settings. Here is a guide for using startupmanager:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")
The setting you want to change is the "show bootloader" option.

If you want to edit menu.lst manually, there is a section explaining that as well. You will want to uncomment (remove the # symbol) from "hiddenmenu" and set the "timeout 10" to a lower number.

---

### Post by dave collin on 2009-09-06
Ok, thanks people.
Dave

---

