---
title: "I broke ubuntu, now I get error 24 on boot"
date: 2009-08-06
forum: General Help
---

### Post by Random21 on 2009-08-06
Yesterday, I was splicing together parts of movies from my external drive (procedure: copy cd1 and cd2 from external to internal disk, use mencoder to splice in the terminal, transfer back, delete everything except output file, empty trash periodically).  At some point things started to act funny.  When I tried to unmount the disk, it wouldn't allow me to do it through the gnome, it would pop up an empty dialogue box.  I then tried to get back into the terminal, but that would be an empty box too.  I tried several different things, all new applications were empty boxes.  Tried to open things using alt+f2 which would open the box and allow me to enter text/select a program, but would never open the thing.  Going to other workspaces (or whatever you call ctrl+alt+f1-6) didn't work because I couldn't login; it would just hang after I entered my username.

My solution: reboot.

On reboot I get "Error 24: you f'ed it up" (loosely translated)

I have tried to fix it by changing the hd(0,X) but that didn't work.  x=0,2,3 error 17, x=4 flashes kubuntu then has some issues and stalls.  Other people have gotten this error by updating the kernel, but I am not sure if I did that or not (I don't pay too much attention to the long list of updates).  Booting into kubuntu from the normal grub entry works just fine.

Partitions
sda1 - Swap
sda2 - Ubuntu
sda3 - Empty
sda4 - Files
sda5 - Kubuntu

Grub list

```

title           Ubuntu Jaunty
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=065e8b1f-2f1e-4e02-93cd-ffd062cb0b60 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
savedefault
boot


title           Ubuntu Jaunty (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=065e8b1f-2f1e-4e02-93cd-ffd062cb0b60 ro single
initrd          /boot/initrd.img-2.6.28-11-generic
savedefault
boot
```

---

