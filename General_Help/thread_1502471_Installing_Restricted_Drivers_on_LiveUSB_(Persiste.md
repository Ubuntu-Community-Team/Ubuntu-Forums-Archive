---
title: "Installing Restricted Drivers on LiveUSB (Persistent install)"
date: 2010-06-05
forum: General Help
---

### Post by RJ12 on 2010-06-05
Ok, so I made a quick little USB install of Ubuntu using the USB Creator thing in Ubuntu 9.10 (I gave it room to store data also). I use this USB on two computers (Both Toshiba Laptops) and one of them needs restricted drivers for 3D. If I install them, will it mess up where it won't work on any other computers?

---

### Post by sdennie on 2010-06-05
In this case, yes, probably.  The file that will need to be modified is /etc/X11/xorg.conf.  On many (or most) machines that file doesn't exist because it can be deduced at runtime.  If you install something like the nvidia proprietary drivers, it will create that file and explicitly state that you need to load the nvidia driver.  If it fails, you will be left at an "X failed to load" dialog from the vesa driver.

One thing you could do would be to add a script to add an init script (or upstart probably) that runs before X tries to start and either erases the file if need be or copies the file with the proprietary driver into /etc/X11/xorg.conf.

---

### Post by RJ12 on 2010-06-05
I guess maybe an easier thing to do would be to have a USB Flash Drive separate for this machine.


Thanks for the reply though! I guess I will go ahead and mark this as solved

---

### Post by C.S.Cameron on 2010-06-05
There used to be an utility in the repositories named switchconf.
You could switch between different xorg.conf files at bootup.
You could choose between say Nvidia drivers or not, but you could not switch between Nvidia and ATI.
I'm not sure if switchconf works with grub2 or not. I last used it I recall with 8.04.

---

