---
title: "'no loaded kernel'"
date: 2009-12-27
forum: General Help
---

### Post by podkayne on 2009-12-27
I've recently fielded a number of bootloader errors, including apparently the total absence of a bootloader, since I stopped dual-booting Windows XP and Ubuntu 9.10 and tried running Ubuntu only.

The latest issue appears when I try to boot from the GRUB command line and receive the response 'no loaded kernel'. I simply don't understand why I receive this message, and can't seem to locate a way through the issue or understand the resources I find, since I never work at this level otherwise and am very ignorant of these workings. For the time being I can only boot from the CD drive, although apparently the contents of the hard drive are otherwise intact. Would anyone have advice for me? A pointer to a good primer on booting would be cool, too, since the whole topic is beginning to sound very intriguing.

---

### Post by K9. on 2010-02-15
I have the same issue.
Instead of loading as usual when choosing ubuntu instead of xp I get GNU  Grub version 1.97 beta 4 and can't use the command boot

The error: no loaded kernel

9.10 ubuntu

---

### Post by Atrytone on 2010-02-19
Same exact problem for me.

I just installed some updates using the install manager in Ubuntu so I'm guessing one of them caused the problem.

When I power on my machine it gives me the normal grub boot menu where I can choose to boot to my windows or ubuntu. When I choose ubuntu however it gives me the following command prompt:

sh:grub>

and when I try the command 'boot' it gives me the 'error: no loaded kernel' message.

Any advice would be greatly appreciated

---

### Post by Atrytone on 2010-02-19
Also, when I enter the 'ls' command I receive the following:

error: cannot get C/H/S values

I tried following the instructions for booting from grub command line mode[here]("https://help.ubuntu.com/community/Grub2#Command Line & Rescue Mode").  The most I can get it to do is boot back to the grub screen where I can choose which OS to boot to.  Then when I select Ubuntu again it goes back to the same sh:grub> prompt and has not saved any of the changes I made before the reboot.

---

