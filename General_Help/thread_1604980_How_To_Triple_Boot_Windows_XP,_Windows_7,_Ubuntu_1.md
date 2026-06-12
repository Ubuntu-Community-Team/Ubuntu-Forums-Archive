---
title: "How To Triple Boot: Windows XP, Windows 7, Ubuntu 10.04"
date: 2010-10-24
forum: General Help
---

### Post by wah fun on 2010-10-24
I want to have one menu with all three operating systems. I installed XP first, then win 7, then Ubuntu 10.04. Everything works but the bootloader menu is annoying. When the pc boots, the first screen is the grub2 bootloader with an ubuntu entry and a windows loader entry. So, to boot into one of the windows systems, I have to select the windows entry which takes me to the windows bootloader with the xp and win7 entries. I have searched for an answer to this problem but what I have found is too confusing for someone relatively new to linux. I am willing to learn but many posts 'assume' more knowledge than I have. I have installed BCD 2.0.2 but can't really get it to do anything more than what I have already.

So, if someone can either lead me through the process or direct me to a place for assistance, I would really appreciate it.

Thanks in advance for your help.

---

### Post by oldfred on 2010-10-24
The issue is not grub nor Ubuntu but windows. It can only boot from one active (boot flag) partition, so it combines all the boot files into that partition. Then the second install is not directly bootable.

If you are installing you can do this.
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

But you may be able to move boot flag and try repairing the second install, if it is in a primary partition.

---

