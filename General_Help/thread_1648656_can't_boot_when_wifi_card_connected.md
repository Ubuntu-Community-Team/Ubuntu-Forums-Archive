---
title: "can't boot when wifi card connected"
date: 2010-12-19
forum: General Help
---

### Post by kahafeez on 2010-12-19
Hello all,

i installed Ubuntu 10.10 on my desktop computer, the live cd worked fine. my wifi worked there. but after installation completion i didnt get any screen. all black. nothing after the grub menu. i dettached my TP-Link TL-WN353G wireless PCI card and it worked fine. now what to do?
strange, the wifi card works fine on Ubuntu Live CD and on win XP. please guide
i have tried deleting quite and splash during boot up
during boot i pressed 'e' and deleted quite and splash and then ctrl-X but still the same result. the screen goes black. no graphics after grub menu. please advise

---

### Post by kahafeez on 2010-12-19
please reply people, i am having a hard time here ):

Here's my grub:

> 
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --nofloppy --fs-uuid --set 7a326a94-770a-4b65-b7b6-c45fa307c\fcc
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7a326a94-770a-4b65-b\7d6-c45a307cfcc ro  quiet splash
initrd /boot/initrd.img-2.6.35-22-generic


and here is what i have tried already:
press e and delete 'quiet splash' and then boot
press e and replace 'quiet splash' with nomodeset and then boot

nothing works ):

---

### Post by unplugged23 on 2010-12-19
Sounds like some kind of incompatibility problem. I've been having the same problem with a pcie graphics card. I'd be greatfull to hear any solutions!

---

