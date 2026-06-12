---
title: "Error Using Splashy"
date: 2010-02-18
forum: General Help
---

### Post by gunjannigam on 2010-02-18
Hi,
I am using the Ubuntu 9.04 Jaunty Jackalope
I need to change the Usplash screen of ubuntu. For this I have installed a splashy and gsplashy. My splashy doesnt work. Its gives an error

```

Splashy ERROR: Couldn't splashy_start_splashy(). Error -3

```when I run the following command.
```

sudo splashy test

```I think there is some problem with my /boot/grub/menu.lst
This is my menu.lst
```

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        4a0c9816-2a8e-4ed9-a5d5-d25359e39c0b
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=4a0c9816-2a8e-4ed9-a5d5-d25359e39c0b ro vga=792 quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        4a0c9816-2a8e-4ed9-a5d5-d25359e39c0b
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=4a0c9816-2a8e-4ed9-a5d5-d25359e39c0b ro  single vga=792
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        4a0c9816-2a8e-4ed9-a5d5-d25359e39c0b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4a0c9816-2a8e-4ed9-a5d5-d25359e39c0b ro vga=792 quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        4a0c9816-2a8e-4ed9-a5d5-d25359e39c0b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4a0c9816-2a8e-4ed9-a5d5-d25359e39c0b ro  single vga=792
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        4a0c9816-2a8e-4ed9-a5d5-d25359e39c0b
kernel        /boot/memtest86+.bin
quiet

```I dont understand what this error means and what to do next. 
Is there any other way of making my own Usplash??

---

