---
title: "grub 1.99 multi-boot root question"
date: 2012-06-22
forum: General Help
---

### Post by mwl128340 on 2012-06-22
i have 3 os,s installed on my hd. linux mint, ubuntu 12.04, and xp. i am tryiong to use mint as my grub root. i was just wondering what i would have to do to ubuntu grub files(it was the root grub at one point) to have ubuntu grub not take control whan i update. i googled and read a bunch of different things. alough i did see making os_prober a non-executable. i was wondering if this is true and why that is.

---

### Post by oldfred on 2012-06-22
Mint's os-prober will look at the grub.cfg of Ubuntu to update, so you should still update in Ubuntu.

You can make sure Ubuntu's grub2 does not overwrite the MBR on a major update. It remembers where to reinstall.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

You can also add entries to 40_custom to directly boot the newest kernel  using a link that Ubuntu maintains, so you do not have to run the grub update as the kernel updates in Ubuntu will update the link that is used.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

