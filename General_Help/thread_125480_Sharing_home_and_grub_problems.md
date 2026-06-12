---
title: "Sharing /home and grub problems"
date: 2006-02-04
forum: General Help
---

### Post by Pancetilla on 2006-02-04
Hi everybody.

I've got XP and Ubuntu 5.10 installed in my desktop. My /dev/hda is partitioned this way:

/dev/hda1 Windows XP
/dev/hda2 Swap
/dev/hda3 / 
/dev/hda5 /home 
/dev/hda6 free 

I tried to install Frugalware 0.3 (DVD) in /dev/hda6 last night. I intended to install / on /dev/hda6 and use /dev/hda5 as home too. The installation went allright except one of the spanish additional lang-packages, it made my installation stop. So I deselect that package and went on. I installed grub on /dev/hda (overwriting Ubuntu's GRUB, my first error). When I rebooted the machine, I only had this error message:

GRUB GRUB GRUB GRUB

So i boot the PC with a Live CD (Kanotix) and tried to restore my grub from there. I mount frugalware and chrooted to frugalware and tried

grub-install /dev/hda

but an error message appeared, telling me there were no such device. So I mounted Ubuntu instead, chrooted and everything went fine.

I rebooted my machine and Grub was Ok, but when I get to the login screen, my /home was broken. So, I must have made a mistake somewhere along the way. 

Here are my two questions

1.) Is it possible to share /home? I mean, mount /home for two different distros in the same place. I can live without doing this, anyway.

2.) What have I have to do to get GRUB right?

Thanks in advance and apologises for my poor english.

---

### Post by dcstar on 2006-02-04
[QUOTE=Pancetilla]Hi everybody.

I've got XP and Ubuntu 5.10 installed in my desktop. My /dev/hda is partitioned this way:

/dev/hda1 Windows XP
/dev/hda2 Swap
/dev/hda3 / 
/dev/hda5 /home 
/dev/hda6 free 

I tried to install Frugalware 0.3 (DVD) in /dev/hda6 last night. I intended to install / on /dev/hda6 and use /dev/hda5 as home too. The installation went allright except one of the spanish additional lang-packages, it made my installation stop. So I deselect that package and went on. I installed grub on /dev/hda (overwriting Ubuntu's GRUB, my first error). When I rebooted the machine, I only had this error message:

GRUB GRUB GRUB GRUB

So i boot the PC with a Live CD (Kanotix) and tried to restore my grub from there. I mount frugalware and chrooted to frugalware and tried

grub-install /dev/hda

but an error message appeared, telling me there were no such device. So I mounted Ubuntu instead, chrooted and everything went fine.

I rebooted my machine and Grub was Ok, but when I get to the login screen, my /home was broken. So, I must have made a mistake somewhere along the way. 

Here are my two questions

1.) Is it possible to share /home? I mean, mount /home for two different distros in the same place. I can live without doing this, anyway.

2.) What have I have to do to get GRUB right?

Thanks in advance and apologises for my poor english.[/QUOTE]
Start up and use System-Administration-Disks and look at the Partitions, your existing /Home partition may have changed designation.

If so, you may have to modify your /etc/fstab file.

As far as sharing, there is no reason why another distro shouldn't see it (if it can read that particular filesystem type).

---

