---
title: "&quot;no such disk&quot; error following 9.10 install"
date: 2010-01-01
forum: General Help
---

### Post by chrisfields38 on 2010-01-01
I am a complete neophyte with ubuntu, but hope that my experience with the problem described below will be of help to others.

I attempted a full-disk install of ubuntu 9.10 karmic koala from a live CD onto a Gateway MX6124 running Phoenix BIOS v. 70.02.  This machine has a 60 GB ATA hard disk.  

The full-disk install reported no errors.

Following the install, reboot yielded a "no such disk" error from grub, with no grub prompt.

Following instructions for grub re-installation from the live CD given in the online grub2 manual, including the chroot method, did not solve this problem.

After considerable experimentation I determined that installing 9.10 on the full disk, and then re-installing a second time alongside the first install, such that the disk space allocated to the first install was reduced to 29 GB, i.e. just less than half the size of the disk, provides a working installation.  Rebooting after this dual install of 9.10 gave a "no such disk" error but also a grub rescue prompt.  Following the grub rescue instructions in the online grub2 manual, i.e. setting root=(hd0,1), prefix=(hd0,1)/boot/grub, then running insmod /boot/grub/linux.mod followed by linux /vmlinuz root=/dev/sda1 ro followed by boot successfully booted the machine to the first 9.10 install on partition sda1.  After re-installing grub as directed in the grub2 manual, the machine boots normally to the 9.10 install in sda1.  The remainder of this disk appears to be accessible as a mounted filesystem, although I have not attempted to use it. 

I have found no reference to such a problem in the documentation I have examined.  My hypothesis is that the disk controller on this generation of gateway machines cannot deal with an ubuntu installation in which the boot sector is larger than half of the entire disk - hence "full disk" installations on these machines do not work.

If anyone reading this is familiar with this problem and can explain why it occurred, I would be interested.  Thank you.

---

### Post by Leppie on 2010-01-01
i don't think that it's the controller, since you stated that after the 2nd install the system wouldn't boot either.

grub2 is working very well on most systems, however it's still under development. this may cause oddities on some systems. I've seen posts of people having large harddrives assigned to linux with only a small part used for swap and no other partitions on the disk.
another possibility is (and i think this is the more likely one) that there were some errors on your installation cd. the cd should have an autocheck option when booting.

---

