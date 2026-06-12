---
title: "Boot Screen Times Out At Loading Modules"
date: 2006-03-07
forum: General Help
---

### Post by phargarten on 2006-03-07
When I select ubuntu in Grub, it goes to the Ubuntu logo with the progress bar and the first type: Loading Modules. It lags on this and then switches over to the black and white text list of boot materials instead of in the Ubuntu graphic form.

My Grub Code looks like this:

title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/hda7 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot 

Does anyone have any ideaS?

---

