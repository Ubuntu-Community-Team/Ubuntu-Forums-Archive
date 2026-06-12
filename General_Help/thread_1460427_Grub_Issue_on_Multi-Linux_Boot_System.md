---
title: "Grub Issue on Multi-Linux Boot System"
date: 2010-04-22
forum: General Help
---

### Post by Gilliosa on 2010-04-22
I have installed two different variants of Ubuntu and Win7 on a friends laptop. Partitioning is as follows:

Partition 1    Win7
Partition 2    Swap
Partition 3    Ubuntu 8.10
Partition 4    Ubuntu 9.10 Studio

All the OS's are working without fault but in order to boot from Ubuntu 8.10 from Grub, I have to edit the command for the root path from a UUID path to /dev/sda3. This is great and all but having to do it every time we want to boot into 8.10 is quite annoying. Ubuntu seems to be using Grub2 and I have know idea to change the menu.lst like I could with the old Grub. 

Does anyone know how I can change the Grub boot path permanently set to /dev/sda3?

Many thanks!

---

### Post by oldfred on 2010-04-22
Welcome to the forums.

If you are using 9.10 are you not using grub2? or was it an upgrade.
Grub2 is much better at finding other operating systems with sudo update-grub. Grub legacy often required us to manually add a menu.lst stanza for other systems.

If it is just finding the wrong UUID ( I do not know how), you can copy the entry with UUID into 40_custom and edit it at will. then sudo update-grub will add that entry.

If you need more help post this so we can see all the details:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

