---
title: "Dual Booting Help"
date: 2011-02-22
forum: General Help
---

### Post by Nick28th on 2011-02-22
Hi i have Ubuntu 10.1(installed 1st) as my master drive and XP(installed 2nd) as my slave drive and wanted to know how to make it so i could dual boot these. the version of grub on my version of Ubuntu doesn't have the Menu.lys and instead has a grub.lys that i cannot edit. also isn't formatted the same way as menu.lys was. can someone help me get this set up. im new to Ubuntu any help would be much appreciated!!!

---

### Post by quixote on 2011-02-23
Windows bootloader doesn't play nice with others, so the usual way to do it is install other operating systems *after* Windows. What you need to do now is restore the Win bootloader, and then restore grub on top of that.  Instructions here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) (be sure to page down to the Windows restore section).  

After you can boot into Windows, then follow the instructions to get grub working again, which is at the top of that post.  I'm not sure they make that clear enough.

More than you ever wanted to know about grub2 is in the Community Documentation: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

The two main files you edit in grub2 are /etc/default/grub and /etc/grub.d/40_custom or any of the other files in that directory.  The grub2 docs discuss how to do it.  After editing, you run "sudo update-grub" (without quotes) to make the changes take effect.

---

