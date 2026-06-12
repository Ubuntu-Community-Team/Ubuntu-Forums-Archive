---
title: "How to make grub choose OS to boot."
date: 2012-07-24
forum: General Help
---

### Post by dagroves on 2012-07-24
I have two Hard Drives. One has Windows 8 Release Preview, the other one has Ubuntu 12.04 with Gnome 3 on it. How do I make Grub see both and give me the option of what Hard Drive and OS I want when I boot my computer?

---

### Post by jonnyboysmithy on 2012-07-24
So you are only seeing one OS in the grub menu?

If you do ```
sudo update-grub
``` it will update the grub menu.
Say if you installed windows 8 preview after ubuntu then that will add it to the menu.

---

### Post by Mark Phelps on 2012-07-25
What MIGHT work is the following:
1) Boot from the Ubuntu drive
2) Open a terminal and enter "sudo update-grub"
3) Watch the results and see if it displays something like "Windows Loader on SDx".  If it does, it found Win8 and added an entry for it.  If it does not, the os_prober can not recognize Win8.

---

### Post by oldfred on 2012-07-25
Just be careful trying to share any files.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by dagroves on 2012-07-26
> **Mark Phelps said:**
> What MIGHT work is the following:
1) Boot from the Ubuntu drive
2) Open a terminal and enter "sudo update-grub"
3) Watch the results and see if it displays something like "Windows Loader on SDx".  If it does, it found Win8 and added an entry for it.  If it does not, the os_prober can not recognize Win8.

Did this and I guess it is already there! I just did not see it. Thanks! =-]

---

