---
title: "More Operating Systems?"
date: 2006-02-28
forum: General Help
---

### Post by Mau on 2006-02-28
Hi guys,
I'm interested in installing more Linux distributions than just (K)Ubuntu.  It's not that I dislike Ubuntu, but I would like to see Linux from a different angle.

When I installed, I put my home folder on a whole separate partition (at least I think I did).  Would this make it easy to install another distribution running alongside Ubuntu and XP?  Is this something that I would even want to do -- would I experience any difference?

Thanks.

---

### Post by o_fortuna on 2006-02-28
[QUOTE=Mau]Hi guys,
I'm interested in installing more Linux distributions than just (K)Ubuntu.  It's not that I dislike Ubuntu, but I would like to see Linux from a different angle.

When I installed, I put my home folder on a whole separate partition (at least I think I did).  Would this make it easy to install another distribution running alongside Ubuntu and XP?  Is this something that I would even want to do -- would I experience any difference?

Thanks.[/QUOTE]
I have done the same thing. Trying other distros is great becuase everyone is different and different distros appeal to different people. And, having /home on a separate partition certainly makes sharing data easy. The most important thing is to back up data whenever dealing with partition changes. The chances of something happening are pretty small, but still, you want to be safe.

---

### Post by Jucato on 2006-02-28
If you have some space to spare, I recommend creating a 5GB space to "test" drive other distributions. if all you want to do is really to test them and not to work with them full time. IMHO, 5GB would be enough for a basic Linux install ( 4GB main +swap).

Having a separate /home partition is very handy, especially when you need to reinstall the system. However, I don't think it would be advisable to have two different Linux distributions share the same /home partition, since different distros install different hidden folders in your /home directory for configuration, and might cause conflicts.

---

### Post by Freddy on 2006-02-28
I would recommend also to backup your existing grub configure file or use your current one. I installed Kubuntu in a third install and choosed to reinstall grub and the install found my previous XP and Fedora and tried to configure grub to be able to boot up all three systems but after a reboot only Kubuntu and XP booted.

This is not a major problem it's fairly easy to configure grub yourself but if you have made some changes to your conf file, back it up just in case.   /// Freddan

---

### Post by Mau on 2006-02-28
Okay - I'm glad it sounds like something that is entirely possible.  I think I will kill some space off my Windows partition (now that I think of it, I haven't booted into Windows since I installed Kubuntu -- wasted space I think).

---

### Post by Jucato on 2006-02-28
Yeah. I'd leave Windows with about 10GB space tough, depending on how many apps you have installed. XP is a byte-hungry beast. I just noticed how it consumed 3-4 GB space on a fresh install, and almost 5GB once I've upgraded to Service Pack 2. Compare that to my Kubuntu, which uses about 3 GB NOW, updated, installed with more than a dozen programs. :D

Might I also suggest a third way to preserve your GRUB, no matter how many times you reformat/reinstall OS'es. Install GRUB on a floppy disk and set your system to boot from floppy. This way, even if by some unfortunate instance that the MBR of any of your hard drives is modified, your system will still boot properly. Also take note that the menu.lst that GRUB will be using will be found in the /boot/grub of the OS that installed it.

---

### Post by nobar on 2006-02-28
Another approach would be to use the free VMware Player [http://www.vmware.com/products/player/](http://www.vmware.com/products/player/).  You could run Ubuntu as your host and experiment with as many "virtual" linux distributions as you want.  If you need to share files between your home directory on Ubuntu and the virtual linux boxes, you can use Samba or scp (both your host Ubuntu and the guest Linux will be running at the same time on the same PC).

The setup I describe will result in some (usually minor) perfomance limitations in the virtual machine and it doesn't fully test hardware compatibility of the guest O/S, but it is a safe and easy way to experiment with the applications and user-interface features provided by various Linux distributions.

Note: You need a pre-existing VMware virtual machine to make this work.  You can download these from the VMware web site.  Once you have a virtual machine, you can install the O/S of your choice onto the virtual machine just by "virtually" booting from an installation CDROM or ISO.

---

### Post by Jucato on 2006-02-28
either that or use the free VMWare Player, and use Qemu to make the virtual machine. There's a guide here somewhere. You can just dig it up.

---

