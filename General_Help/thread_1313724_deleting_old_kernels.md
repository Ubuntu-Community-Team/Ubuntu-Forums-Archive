---
title: "deleting old kernels"
date: 2009-11-04
forum: General Help
---

### Post by chinna saaeb on 2009-11-04
I am using ubuntu 8.04 LTS and on another 9.o4.
I periodically update the OS.
As a result in the boot menu I have many kernels being shown.

I want to delete the old stuff and also edit the grub menu (menu.lst)

I red hat i would do it using 
rpm -ev kernel...

How can it be done in ubuntu without affecting the system

---

### Post by IllegalCharacter on 2009-11-04
You can look at the list of kernels installed in Synaptic (System -> Administration -> Synaptic Package Manager) and searching for linux-image. Then you'll see a whole bunch of packages like linux-image-2.6.xx-xx-generic. You'll probably have the latest one installed (as of this writing it is 2.6.31-14) and a bunch of others. You can remove those if you want.

As for the GRUB menu, you can edit menu.lst by going to a terminal and typing
```
gksudo gedit /boot/grub/menu.lst
```There you can remove the older entries.

---

### Post by lidex on 2009-11-04
Another route is installing ubuntu-tweak which does alot of neat things. Info [here]("http://ubuntu-tweak.com/downloads"). With it you can easily view and remove kernels. Grub will be automagically updated as is the case when using synaptic.

---

### Post by chinna saaeb on 2009-11-04
Thanks Illegal Character
solved it

---

### Post by Claus7 on 2009-11-04
Hello,

nice that you solved it. Also do not forget to remove manually the info of the old kernels from your /boot directory. If you have given it the recommended amount of space (100MB), then with the update of the kernels it will fill that space in no time.

Regards!

---

### Post by grandtoubab on 2009-11-04
I think it safer to use Synaptic to manage your packages

---

### Post by m4tic on 2009-11-04
Lol the illegal guy help you

---

