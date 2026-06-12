---
title: "Error 15 File not found at Boot Option"
date: 2010-06-19
forum: General Help
---

### Post by krenault on 2010-06-19
Hi

I have a problem with my Ubuntu 9.10. I found on some help forum on how to clean up the boot menu some of the options for previous updates. 
The link for the help is 

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

So I went to terminal, typed gksu gedit /boot/grub/menu.lst

and on that file deleted the extra menu options, leaving 

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        507cefd1-74f3-489a-920a-d588e36b6476
kernel        /vmlinuz-2.6.31-22-generic root=UUID=8c8819d1-2861-419a-99cc-2c0fed37e1c8 ro quiet splash 
initrd        /initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        507cefd1-74f3-489a-920a-d588e36b6476
kernel        /vmlinuz-2.6.31-22-generic root=UUID=8c8819d1-2861-419a-99cc-2c0fed37e1c8 ro  single
initrd        /initrd.img-2.6.31-22-generic


Aside from doing this to my ubuntu, I also deleted some files on /boot folder because my update said there's no room. I deleted the files through nautilus leaving only the two folders. 

Now, after restarting my ubuntu, I couldnot boot back into ubuntu. After reaching the boot menu and choosing the "Ubuntu 9.10, kernel 2.6.31-22-generic" option, I get a new black screen with these in white letters

Boot from (hd0,5) ext3 507cefd1-74f3-489a-920a-d588e36b6476

Error 15 : File not found

Press any key to continue ... _

Pretty much I'm sure I couldn't go into my ubuntu because of these two things. It would be really helpful if someone give me some advice. Thanks

---

### Post by krenault on 2010-06-19
Also I forgot to mention that I try to update to the new 10.04 Ubuntu system but it never fully finish because of space problem (hence while i deleted the files from /boot). Perhaps that is the problem?

---

### Post by Tim Sharitt on 2010-06-19
The problem is that you deleted the Linux kernel, which you really, really need. This post should get you going again: [http://ubuntuforums.org/showthread.php?t=1034523](http://ubuntuforums.org/showthread.php?t=1034523)

In the future, do not delete stuff if you don't know what it is or what it does (especially if you need to be root to do it) ;)

---

### Post by krenault on 2010-06-20
Right I could follow every step of the link you suggest except that the kernel number has changed. I have no idea what code i should use. 

In the link it's replacing 2.6.22-14-generic

when I tried to follow the step in reply 5 of that thread, with this command, 

apt-get purge linux-headers-2.6.22-14-generic linux-image-2.6.22-14-generic linux-restricted-modules-2.6.22-14-generic linux-ubuntu-modules-2.6.22-14-generic

it says 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.22-14-generic

Is there a way to find out which version of kernel my cd have?

Thanks

---

