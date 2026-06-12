---
title: "Booting to text mode via grub"
date: 2009-10-31
forum: General Help
---

### Post by batshwa on 2009-10-31
Hi,

I recently installed Xubuntu 9.10 and I am using grub for dualbooting.  I now wanted to ask if it is possible to use grub to boot directly into text mode (without starting services like cups, appArmor etc, which is the case when I use the kernel parameter `text').

I have also tried appending `init=/bin/bash' to the kernel line, but this did not have the desired effect.

If it is of any help, my menu.lst currently has the following entries:

```
title        Ubuntu 9.10, kernel 2.6.31-14-generic (text mode)
uuid        e22dec4a-be39-4129-95d9-9b4ac4c4a841
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e22dec4a-be39-4129-95d9-9b4ac4c4a841 ro noquiet nosplash text 
initrd        /boot/initrd.img-2.6.31-14-generic
```Many thanks in advance!

---

