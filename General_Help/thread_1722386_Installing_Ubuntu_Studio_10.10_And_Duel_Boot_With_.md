---
title: "Installing Ubuntu Studio 10.10 And Duel Boot With Windows 7. (Separate Hard Drives)"
date: 2011-04-05
forum: General Help
---

### Post by Tman5293 on 2011-04-05
Hi,

I want to set up my PC so that I have Windows 7 installed on one hard drive and Ubuntu Studio installed on a completely separate hard drive. I currently have both hard drives installed in my PC and the larger one (640GB) has Windows 7 installed and is currently taking up that entire drive. My other hard drive (160GB) has a wubi install of Ubuntu 10.10 on it so it shows up on the Windows boot menu. What I want to do is wipe the smaller hard drive and install Ubuntu Studio on it and have it show up in the boot menu just like my wubi install does. If anyone can tell me the steps I need to take to make this happen it would be greatly appreciated. 

I need to know things like:

1. When I install Ubuntu Studio, do I install the boot loader to the MBR of the hard drive I'm installing it on?

2. How exactly do I add Ubuntu Studio to the Windows boot loader?

Thanks,
Tman5293

---

### Post by Tman5293 on 2011-04-05
Anybody? I could really use some advice on this.......:(

---

### Post by oldfred on 2011-04-05
Windows boots wubi because it is inside the windows partition. But windows will not easily boot another system.

Grub2 easily boots many systems. Does Studio use grub or grub2? Not familiar with Studio. 

You should use gparted to manually set up partitions on the second drive and then use manual install. That will give you the choice to install grub to the second drive.

This is for standard Ubuntu:
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

There is another third party boot loader that boots windows from the windows partition and will add Ubuntu. I have never used it, I like grub2, but some have said it works.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---

### Post by Tman5293 on 2011-04-05
> **oldfred said:**
> Windows boots wubi because it is inside the windows partition. But windows will not easily boot another system.

Grub2 easily boots many systems. Does Studio use grub or grub2? Not familiar with Studio. 

You should use gparted to manually set up partitions on the second drive and then use manual install. That will give you the choice to install grub to the second drive.

This is for standard Ubuntu:
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

There is another third party boot loader that boots windows from the windows partition and will add Ubuntu. I have never used it, I like grub2, but some have said it works.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

Thanks for the reply!

I already had plans of using EasyBCD to edit the Windows bootloader. So if I tell Ubuntu to install GRUB2 on the partition Ubuntu is installed under I should just be able to add it to the Windows bootloader with EasyBCD. I'm still open to other options so If anyone has any ideas for a better way to do this, I'd love to hear them.

---

### Post by oldfred on 2011-04-06
Just install grub2's boot loader to the MBR of the second drive. Grub2 does not like to install to a partition as it is less reliable and I do not think EasyBCD requires it in a partition anymore to chainload. Then you can boot Ubuntu directly on the second drive if windows stops working.

---

