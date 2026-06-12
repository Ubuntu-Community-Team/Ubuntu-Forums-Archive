---
title: "Problem getting Ubuntu s/w to start on triple boot Acer Aspire One netbook"
date: 2011-05-12
forum: General Help
---

### Post by meggiedude on 2011-05-12
OK, So I currently have an Acer Aspire One netbook 120GB drive which came with Linpus lite preloaded. I have  set-up dual boot a year or so ago. It now dual boots to either Linpus or Vista (yes I know!) via the Linpus grub.conf ( I got the instructions I think from here: [http://jargongeneration.com/AcerAspire/index.php](http://jargongeneration.com/AcerAspire/index.php))

I want to get the latest Ubuntu 11.04 build on this as a third boot option. If this work OK I may ditch the Linpus or Vista build at some point.

So I've used Gparted on a USB drive to setup up three extended Logical Partitions (sda5, 6 and 7).

I then loaded Ubuntu s/w via an external drive with
/boot on 100MB /sda5
 Swap on 1GB /sda6
/ on the 40GB+ /sda7

When I was asked for the bootloader location in the Ubuntu install gui I chose /sda5 (out of complete ignorance)

All fine at this point. 
What do I have to get the linpus lite /boot/grub/grub.conf to see and start ubuntu?? Or is there something else I need to do??

Also, how does Ubuntu know which swap partition to use, as there is already one for the linpus lite install.

Thanks in advance

MD

---

