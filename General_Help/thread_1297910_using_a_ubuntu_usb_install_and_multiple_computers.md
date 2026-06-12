---
title: "using a ubuntu usb install and multiple computers"
date: 2009-10-22
forum: General Help
---

### Post by thekidxp on 2009-10-22
I have a windows PC and a macbook pro. I want to install ubuntu on a usb hdd and use it to boot into either computer with it.

How hard will this be?

Will it have trouble recognizing the different setups to boot?

both are intel.

and if it's a ton of trouble I can just install it onto my PC, but it would be nice to be able to boot into ubuntu whenever I need it.

thanks in advance!

---

### Post by Giblet5 on 2009-10-22
> **thekidxp said:**
> I have a windows PC and a macbook pro. I want to install ubuntu on a usb hdd and use it to boot into either computer with it.

How hard will this be?

Will it have trouble recognizing the different setups to boot?

both are intel.

and if it's a ton of trouble I can just install it onto my PC, but it would be nice to be able to boot into ubuntu whenever I need it.

thanks in advance!


On Karmic (9.10), there is a menu option (System/Administration/Create USB Startup Disk) that takes a LiveCD image and creates a 'persistent' LiveCD install.

It works with everything I've tried (sticks, compact-flash cards, USB hard drive).

You can update it, add software, and work off of it.

I wouldn't set up anything that's real machine-dependent though (eg, 3D drivers, Compiz, etc) because they might not work well, one machine to another...


Note that pendrivelinux.com has installable images for doing this easily with LOTS of Linux OSes...

---

### Post by Mighty_Joe on 2009-10-22
> **Giblet5 said:**
> On Karmic (9.10), there is a menu option (System/Administration/Create USB Startup Disk) that takes a LiveCD image and creates a 'persistent' LiveCD install.


That Live USB Creator is available on the 9.04 Live CD and is in the repository for previous versions.  
There are [several other]("http://ubuntuforums.org/showthread.php?t=1193680") ways to install to a USB drive.  I did a full install to a USB drive and haven't had any problems on the 3 computers I've tried it on, but I did not install any restricted drivers, either.

---

### Post by Giblet5 on 2009-10-22
> **Mighty_Joe said:**
> That Live USB Creator is available on the 9.04 Live CD and is in the repository for previous versions.  
There are [several other]("http://ubuntuforums.org/showthread.php?t=1193680") ways to install to a USB drive.  I did a full install to a USB drive and haven't had any problems on the 3 computers I've tried it on, but I did not install any restricted drivers, either.

I still use a stick I made by hand using the selinux.exe bootloader for DOS.

Ahhh. Those were the days. Oh, wait...no...those days sucked!

---

### Post by Mighty_Joe on 2009-10-22
> **Giblet5 said:**
> I still use a stick I made by hand using the selinux.exe bootloader for DOS.


You are a better man than I.  Read through the topic I posted and you'll see me doing this with Grub2:
](*,)

---

### Post by thekidxp on 2009-10-22
I just figured i would check in first to see how tough it would be i think i have a plan of attack now thanks

---

