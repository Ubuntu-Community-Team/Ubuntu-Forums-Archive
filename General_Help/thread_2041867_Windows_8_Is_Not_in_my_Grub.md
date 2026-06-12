---
title: "Windows 8 Is Not in my Grub"
date: 2012-08-13
forum: General Help
---

### Post by khoraski on 2012-08-13
I have Windows 8 CP installed on my laptop as well as Ubuntu, but Windows 8 will not appear in my Grub menu, meaning I cannot boot from it.

I tried updating my Grub, and doing a Boot Repair, but it did not work. 

How could I add it to my Grub in Ubuntu?

I'll add more information if you request it.

---

### Post by drs305 on 2012-08-13
So you have run "sudo update-grub" and also clicked the "Recommended repair" button in the Boot Repair app?

If so, the next step is to run the boot info script from Boot Repair and either post the link or the contents of the file it generates. It will provide us with details of your system's boot files as well as what Boot Repair has already tried to do.

---

### Post by khoraski on 2012-08-13
> **drs305 said:**
> So you have run "sudo update-grub" and also clicked the "Recommended repair" button in the Boot Repair app?

If so, the next step is to run the boot info script from Boot Repair and either post the link or the contents of the file it generates. It will provide us with details of your system's boot files as well as what Boot Repair has already tried to do.

I still have the link from the Boot Repair. I wrote it down,

[http://paste.ubuntu.com/1143508/](http://paste.ubuntu.com/1143508/)

If it helps, Windows 8 is on /dev/sda3

---

### Post by khoraski on 2012-08-13
Is there any more information you need? :I

---

### Post by drs305 on 2012-08-13
Thanks for posting the link. 

I looked at the file but I'm not a Windows user. 

You have the folders and files I would normally look for (/boot, /boot/bcd, and winload32.exe). However, in addition to not being a Windows user, I haven't seen a RESULTS.txt which has a working Windows 8 upgrade in it so I can compare it. So although I can find the files, I don't know if they are on the proper partition or not.

Hopefully a Windows user familiar with 8 will see your post. 

The only question I have is 'What happens when you try booting the Grub Windows entries - especially the second one)?

---

### Post by khoraski on 2012-08-13
> **drs305 said:**
> Thanks for posting the link. 

I looked at the file but I'm not a Windows user. 

You have the folders and files I would normally look for (/boot, /boot/bcd, and winload32.exe). However, in addition to not being a Windows user, I haven't seen a RESULTS.txt which has a working Windows 8 upgrade in it so I can compare it. So although I can find the files, I don't know if they are on the proper partition or not.

Hopefully a Windows user familiar with 8 will see your post. 

The only question I have is 'What happens when you try booting the Grub Windows entries - especially the second one)?

All I had to do was boot into the second one labeled as a Windows' Recovery Environment? O_e

I kinda feel stupid that I didn't try that. I tried the first one, but you know, it was actually the recovery environment so I didn't bother trying the second one (I thought since I have had a different version of Windows in the past, it was just that old recovery partition).

Just one last question, how could I go about changing the labels in the Grub menu? Because that's labeled incorrectly so I'd like to change it.

---

### Post by oldfred on 2012-08-13
With Vista the os-prober used to reverse the recovery & boot partition label confusing everyone. It now looks like with Windows 8, it is just calling everything recovery. Not sure what it sees to know the difference as script does not show anything.

Customizer is the easiest way, but I have used drs305's manual instructions from before customizer existed.
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by drs305 on 2012-08-13
I'd probably use Grub Customizer as well, as it is an easy to use GUI app. It does however rewrite some of your Grub files, so another method is just to create a custom menu. Both options are in *oldfred's* links.

I'm glad you found out it works, and now I have a working RESULTS.txt for Win 8, so it's all good.

When you don't have any other questions about this issue please mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post.

Happy Ubuntu-ing !

---

### Post by khoraski on 2012-08-13
Alright, thanks for the assistance. I'll mark it as solved. 
Now my dual-boot is working perfectly. :D

---

