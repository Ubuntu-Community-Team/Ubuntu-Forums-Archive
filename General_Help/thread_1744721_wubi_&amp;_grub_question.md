---
title: "wubi &amp; grub question"
date: 2011-04-30
forum: General Help
---

### Post by Gianmaria on 2011-04-30
Hi

i discovered now wubi , a ubuntu installer , that i can run from windows

i guess i need a unlocaded space in my hard disk , right?

well my question about wupi , does it let me install the grub load where i want ?

because [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer) does it show that i change the windows loader

i did install ubuntu and i did store the grub on a fat32 hard disk because i don't want to edit windows mbr

can i do this (install grub loader on a fat32 disk) without edit/windows ?

thanks

---

### Post by idoitprone on 2011-04-30
[https://wiki.ubuntu.com/WubiGuide#What](https://wiki.ubuntu.com/WubiGuide#What) is Wubi?
[http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer](http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer))
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Wubi does not require you to unallocate hard space. It uses your 
current windows filesystem which is most likely ntfs. From the installer, you can reserve space for you wubi installation. This implementations has it benefits and it downsides. You should the read wubi guide, since ntfs has some instances of corruption problem with hard reboots or problem with disk fragmentation. 

One advice, go to the synaptic package manger and lock all updates for grub. It will add a problem with boot as I had encountered once.

About the issue with the bootloader
[https://wiki.ubuntu.com/WubiGuide#What happens if I have another bootloader?](https://wiki.ubuntu.com/WubiGuide#What happens if I have another bootloader?) Here is some reading material. Wubi still uses the windows bootloader

---

