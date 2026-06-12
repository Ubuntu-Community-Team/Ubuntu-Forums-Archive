---
title: "how to edit grub"
date: 2006-06-18
forum: General Help
---

### Post by abhijeetnayak on 2006-06-18
hi, 
I have installed mandriva 2006 after ubuntu 6.06 using grub as boot loader. now I am not able to boot into ubuntu, because there is no option for selecting ubuntu.

Can anyone tell me how to add ubuntu to grub menu, so that i can boot into ubuntu.

thanks.
abhijeet

---

### Post by yager on 2006-06-18
Can you post your current /boot/grub/menu.lst file?  

The entry that I have to boot Ubuntu is:

title		Ubuntu, kernel 2.6.15-25-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-686
savedefault
boot

BTW, I am booting from an external drive so the reference to /dev/sda1 would need to be moved to the correct device on your system.

---

### Post by Ramses de Norre on 2006-06-18
```
sudo gedit /boot/grub/menu.lst
``` and add something like this ```
title           Ubuntu, kernel 2.6.15-25-k7
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-25-k7 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-k7
savedefault
boot

```
You might need to change some things, I don't know what kernel you have and where it's installed and so on.

---

### Post by rowanparker on 2006-06-18
Im guessing Mandriva reinstalled grub.
You could either reinstall grub using Ubuntu CD and then boot grub and add an entry for Mandriva. Or you could could boot Mandriva and do what Ramses de Norre said.

Rowan.

---

