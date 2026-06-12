---
title: "Downgraded kernel does not show up in the boot menu."
date: 2009-11-07
forum: General Help
---

### Post by wulfgang on 2009-11-07
Hello,
I recently downloaded the .deb packages from this [ubuntu link]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") which are various linux kernels.
It downloaded and installed fine(with gdebi) but the kernel I downloaded (2.6.15) Is not showing up in the boot menu.
Is there anything else I need to do?
Any help will be much appreciated. ;)
EDIT: Downloaded 2.6.32-3 from this link:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-image](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-image)

---

### Post by wulfgang on 2009-11-07
Bump, sorry.

---

### Post by wulfgang on 2009-11-07
bump...

---

### Post by drs305 on 2009-11-07
Have you tried running 
```
sudo update-grub
```
to see if Ubuntu automatically picks up the new kernel?

---

### Post by wulfgang on 2009-11-07
No, that didn't work. :(

---

### Post by drs305 on 2009-11-08
Next you can check to see if the new kernel is in /boot along with your newer kernel (or any kernel that you have installed that works from the Grub menu). You can check with a file browser or run this command:
```

ls /boot/vmlinuz*

```
If you find the kernel you want there, open /boot/grub/menu.lst and copy/paste one of the current selections and change the kernel and initrd lines to reflect the new kernel designation (i.e. replace -13 with -9, etc). 

A complete section looks like this:
> title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0fc4d6eb-f64d-4e4e-aef6-1f274aeab67c ro 
initrd		/boot/initrd.img-2.6.24-19-generic

```
gksu gedit /boot/grub/menu.lst
```

Check the "default 0" line in menu.lst and change it to the correct number. If you plan on using this new kernel, place the entry at the top of the list of choices (not the top of the file) and "default 0" will boot to your "new" addition.

If you have questions, post your menu.lst and the kernel you want to add and we can help out.

---

