---
title: "Grub boot order"
date: 2009-09-07
forum: General Help
---

### Post by djbeadle on 2009-09-07
Ok, I have used windows all my life (13 years) and am looking to branch out into other OS. I am currently running Xubuntu for this post and it works fine. My question is not about Xubuntu, but about Grub. When i get to the grub, it shows me this:

```
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/memtest86+.bin
quiet
```This is taken directly from boot/grub/menu.ist. The first two "clumps" of code belong to (i believe) Ubuntu, which i recently installed on my computer, but doesn't run that well, so i just use Xubuntu. [COLOR=Red]Note: [COLOR=Black]even though it says it's all Ubuntu, all of the clumps of code (or segements) belong to Xubuntu.
[/COLOR][/COLOR]
So, the default, it automatically boots into Ubuntu, which i don't want it to do. I want it to boot into Xubuntu by default.

Can i just cut and paste the clumps of code to put them in the order i want(probably not, but just checking)? Or is there a different way to do this that i don't understand. 

I googled changing boot order Xubuntu, but it tells me to change the default code order that i don't understand what i need to change.

Thanks!
Djbeadle

---

### Post by lildigiman on 2009-09-07
This is Normal. Choose the first one of the menu. The rest are older Kernel versions OR a recovery system for that kernel.

---

### Post by djbeadle on 2009-09-07
Choose the first of the menu... that will just boot that item. I want to change the order of the default boot.

---

### Post by drs305 on 2009-09-07
You can edit /boot/grub/menu.list and edit the line that reads:
> 
default 0

You will have to open an editor with admin powers (root).

0 is the first menu item of the group. 1 is the second. So if you want to boot to the third entry (the third "title"), change the value to 2.

I wrote a guide about StartUp-Manager, a GUI app that tweaks lots of settings without having to manually edit things. I believe it works in Xubuntu but even if not there is a lot of info about how menu.lst works. It also explains how to remove extra kernels if you feel you don't need so many.

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by DeMus on 2009-09-07
> **djbeadle said:**
> Ok, I have used windows all my life (13 years) and am looking to branch out into other OS. I am currently running Xubuntu for this post and it works fine. My question is not about Xubuntu, but about Grub. When i get to the grub, it shows me this:

```
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2fe54e6b-5d26-401f-8be8-008462ecd94b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2fe54e6b-5d26-401f-8be8-008462ecd94b
kernel        /boot/memtest86+.bin
quiet
```This is taken directly from boot/grub/menu.ist. The first two "clumps" of code belong to (i believe) Ubuntu, which i recently installed on my computer, but doesn't run that well, so i just use Xubuntu. [COLOR=Red]Note: [COLOR=Black]even though it says it's all Ubuntu, all of the clumps of code (or segements) belong to Xubuntu.
[/COLOR][/COLOR]
So, the default, it automatically boots into Ubuntu, which i don't want it to do. I want it to boot into Xubuntu by default.

Can i just cut and paste the clumps of code to put them in the order i want(probably not, but just checking)? Or is there a different way to do this that i don't understand. 

I googled changing boot order Xubuntu, but it tells me to change the default code order that i don't understand what i need to change.

Thanks!
Djbeadle

How did you install Xubuntu? Did you download a CD and install from there, or did you install Ubuntu and later on you installed the XFCE package to make it become Xubuntu?
If it is the latter you have to do this:
when booting you wait for the log in screen.
When it appears you also see a little box saying something about options and which version to boot into.
Choose Xubuntu there and make it permanent, not only for this time.
From now on you will boot into Xubuntu.

This however has nothing to do with Grub or the kernel, it is the same for both distro's.

---

### Post by djbeadle on 2009-09-08
> **DeMus said:**
> How did you install Xubuntu? Did you download a CD and install from there, or did you install Ubuntu and later on you installed the XFCE package to make it become Xubuntu?
If it is the latter you have to do this:
when booting you wait for the log in screen.
When it appears you also see a little box saying something about options and which version to boot into.
Choose Xubuntu there and make it permanent, not only for this time.
From now on you will boot into Xubuntu.

This however has nothing to do with Grub or the kernel, it is the same for both distro's.


No, i downloaded the iso, burned it to a disk, booted from the disk and installed. Later i installed Ubuntu. 

On a side note, i also have win xp running on this computer, so if that matters let meknow amd i cam give you more info.

---

