---
title: "Removing an unwanted 9.10 install and correcly updating grub."
date: 2009-12-20
forum: General Help
---

### Post by hephastion on 2009-12-20
This is kinda embarrassing...

I've an old but trusty Thinkpad T43 with Windows XP and Ubuntu 9.10 on it... twice.

I mistakenly let the battery run all the way down while booted into Ubuntu and it apparently hibernated. After this I cold not boot back into Ubuntu. I searched or a solution online and finally gave up, electing instead to re-install Ubuntu. I did this, thinking I was simply wiping my old installation (the disk tool used during the install seemed to indicate this would happen...).

Instead what happened was that the install created a new Ubuntu installation and repaired the old one. I now have three Operating Systems on my laptop, one XP and two Ubuntu 9.10s, all available and working from the GRUB boot menu.

I'd like to just delete the new Ubuntu installation, leaving the old XP and Ubuntu in place and selectable via grub. I created a GPARTED live CD and was planning to simply boot from that and delete the new Ubuntu install and associated swap partition. I was then going to resize the original Ubuntu partition to reclaim the space. Then I got to thinking...

If I just delete the new Ubuntu install, will Grub be left in a state of confusion? Will I have an unbootable machine? Will gparted ruin the existing Linux partition?

I've attached my /etc/mtab and the output of "sudo fdisk -l".

I've also attached the grub menu.lst from the original Ubuntu install and grub.cfg from the new install (The original install is an upgrade and is apparently using a different version of grub than the new install, which was from scratch).

Anyone know how I can safely remove the new install, reclaim the space, and leave grub in a good state?

Thanks,
James

---

### Post by oldfred on 2009-12-20
You have to decide which install you want and whether you want grub legacy or new grub.

Since your old install seems to be repaired you can boot into it and just to a reinstall of old grub from that. You will not be able to boot the new install (unless you edit menu.lst)

If you are in your old Ubuntu you can install grub easily, the find should just be your current partition, adjust the root to :
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,5)
root (hdx,y) #use the numbers from the previous command
setup (hd0)

---

