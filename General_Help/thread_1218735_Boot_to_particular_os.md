---
title: "Boot to particular os"
date: 2009-07-21
forum: General Help
---

### Post by philgozdowski on 2009-07-21
how do i choose to boot to a specific os if i have more than one

new, thanks

---

### Post by philcamlin on 2009-07-21
if you have windows installed then you have ubuntu installed a "bootloader" will show up showing you the 2 os's and will let you choose wich one to install :popcorn::popcorn:

---

### Post by lisati on 2009-07-21
Assuming you've just intstalled Ubuntu, you'll be presented with a menu with a list of OSes. Use the up and down arrows to highlight the OS you want to boot, and press "Enter"

---

### Post by philgozdowski on 2009-07-21
need to choose between ubuntu and crashbang as primary os

---

### Post by lisati on 2009-07-21
> **philgozdowski said:**
> need to choose between ubuntu and crashbang as primary os

It might help if we know what choices you are presented with when you power up your computer.

---

### Post by philgozdowski on 2009-07-21
crashbang kernels and ubuntu kernels, and it boots to crashbang auto if i dont make any selection because i installed it last

---

### Post by philcamlin on 2009-07-21
boot into live cd and reinstall grub if you have ubuntu installed :popcorn:

---

### Post by cariboo on 2009-07-21
You need to edit /boot/grub/menu.lst to set which os starts by default, if Ubuntu is the third choice in the menu, you need to set the default to 2. to Edit /boot/grub/menu.lst, press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

this opens the text editor as root and allows you to edit the file. Look for a line that says:

```
default     0
```

If Ubuntu is the third choice in the list change the line so it looks like this:

```
default     2
```

then save and exit, once you reboot, Ubuntu should boot by default.

---

