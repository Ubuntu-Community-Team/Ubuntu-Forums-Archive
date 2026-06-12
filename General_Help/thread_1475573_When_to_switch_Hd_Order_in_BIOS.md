---
title: "When to switch Hd Order in BIOS"
date: 2010-05-07
forum: General Help
---

### Post by sandman3838 on 2010-05-07
Hello

I'm getting ready to install Ubuntu 10.04 on my second SATA HD.

For now my Boot order is

Winxp/Win_7 are on my 1st HD.

Ubuntu (soon to be) is in second place.

I remember reading somewhere that I need to switch the boot order?

Do I do this before or after I install Ubuntu?

Thank you.

---

### Post by rnerwein on 2010-05-07
hi
you only have to switch the boot order in bios to set it to boot from CD ( for installing only ). some times even that you
mustn't change it there. try first with the install CD  already in your CD/DVD drive when booting. if your box don't boot
from the CD you have to change the boot order in your bios.

ciao

---

### Post by sandman3838 on 2010-05-07
No! No!

It's not that I can't access or boot to the CD, I have no issues there.  It's the HD boot order not which device gets the first second third boot!

For Windows to run/install it needs to be the primary HD.
Once you install Ubuntu to another HD its MDR with Grub Menu takes control.  In order for everything to run smoothly so that you can access more than one OS you need to switch the HD boot order.  My question is do I make the switch before or after installing ubuntu?

---

### Post by oldfred on 2010-05-07
I do not think it matters. 
You must, on screen #8 use the advanced button (I missed it on my first beta install) and choose sdb as the drive you want to install grub to.

When I installed Lucid it just defaulted to install grub sda even though I am booting from sdc for Karmic. But that worked well since I can boot either easily. And updates to both grubs show all systems. Since my permanent install will be on sdc I will reinstall grub 1.98 to sdc, but since I am still mostly on Karmic I have not reorganized.

---

### Post by plucky on 2010-05-07
> My question is do I make the switch before or after installing ubuntu?

You won't be able to boot the second hard drive until Ubuntu install writes grub to MBR of that drive.So I would say after you have installed Ubuntu.

Be careful as the default install to the MBR is to the first drive in your system,which is not what you want.Do what oldfred specified

Windows would have written its boot loader to the MBR of the first hard drive,so you can still boot windows if for some reason grub messes up, you just have to change the sequence in the BIOS.
If everything goes ok with the Ubuntu install,you should then get the grub screen to select which operating system you want to boot.


Good Luck

---

