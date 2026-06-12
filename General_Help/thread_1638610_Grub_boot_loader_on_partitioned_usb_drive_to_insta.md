---
title: "Grub boot loader on partitioned usb drive to install distro's?"
date: 2010-12-05
forum: General Help
---

### Post by rick3878894 on 2010-12-05
I am the tech guy in my circle of friends. So almost every body I know uses linux and has a distro that matches their computer specs. 

My gaol is simple and I would like you to read my plan and see if you can spot any thing I am missing before I get to it. 

Use gparted to break up my 4 GB usb flash drive into four partitions.

sdb1 100 MB FAT 16 as a place install a grub boot loader. Flag it as boot. 
sdb2 700 MB FAT 32 Distro "A"
sdb3 950 MB FAT 32 Distro "B"
sdb4 2.1 GB FAT 32 Distro "C"

From there I will use an archive manager to extract the iso's to their respective partitions. 

Then I plan to install the grub boot loader onto sdb1. I have noticed the many command line utilities for grub and plan on reading up on each of them; but, before I set out in learning every thing there is to know about the grub2 boot loader. Am I over estimating the abilities of grub? IF so how does unetbootin do it?

So does my idea work theoretically? Do you see in  pit falls I should look out for?

Once/if I get it all figured out I will write a step by step how to on this subject.

---

### Post by C.S.Cameron on 2010-12-05
There is a tool for doing what you want to do, more or less.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

