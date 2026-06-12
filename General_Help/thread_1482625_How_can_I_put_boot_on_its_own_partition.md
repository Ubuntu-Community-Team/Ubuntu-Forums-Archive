---
title: "How can I put /boot on its own partition?"
date: 2010-05-13
forum: General Help
---

### Post by alienprdkt on 2010-05-13
Updated to lynx fix problem with grub2 now I want to put /boot on its own partition...

Help me out please.

I have gparted can i use the option resize/move then create another partition and copy paste /boot to that partition and edit fstab?

even though fstab hasn't been mounting all of my drives and had to write a custom script to mount / unmount upon startup and shutdown... (what a pain that was)

anyways can this be done... would like to put /boot all on its own in hopes of making it easier for next upgrade! that grub 2 error was something else.

Thanks in advance,

---

### Post by wilee-nilee on 2010-05-13
> **alienprdkt said:**
> Updated to lynx fix problem with grub2 now I want to put /boot on its own partition...

Help me out please.

I have gparted can i use the option resize/move then create another partition and copy paste /boot to that partition and edit fstab?

even though fstab hasn't been mounting all of my drives and had to write a custom script to mount / unmount upon startup and shutdown... (what a pain that was)

anyways can this be done... would like to put /boot all on its own in hopes of making it easier for next upgrade! that grub 2 error was something else.

Thanks in advance,

This is not a good idea I suspect you don't quite understand what happened and the user error that was the cause of it. So in actuality by trying to do it this way, because you don't understand digging a pit that may be the downfall of the operating system, possibly. Grub will only go where you want it to.

---

### Post by alienprdkt on 2010-05-13
> **wilee-nilee said:**
> This is not a good idea I suspect you don't quite understand what happened and the user error that was the cause of it. So in actuality by trying to do it this way, because you don't understand digging a pit that may be the downfall of the operating system, possibly. Grub will only go where you want it to.

hmm well i thought that I could install it to any drive via grub-install /dev/(drive i want grub on)

i just wanted to make it easier to be able to map to the boot partition. I don't know what happened for me to get the error actually, I had selected to install to /dev/sda1 during the upgrade and did the dame upon the fix grub-install /dev/sda1 ... would have been nice to have the opt. to keep local grub config files.

---

### Post by wilee-nilee on 2010-05-13
> **alienprdkt said:**
> hmm well i thought that I could install it to any drive via grub-install /dev/(drive i want grub on)

i just wanted to make it easier to be able to map to the boot partition. I don't know what happened for me to get the error actually, I had selected to install to /dev/sda1 during the upgrade and did the dame upon the fix grub-install /dev/sda1 ... would have been nice to have the opt. to keep local grub config files.

Grub2 automatically creates the grub.cfg file in the main bootable partition, but when asked where do you want grub it is talking about the grub that should only go to the MBR of the HD your installing to IE sda not sda1 or any other #. Now you have to know which drive your installing to, so if you had 2 HD's and you were installing to the second it would probably be called sdb so grub would only go to the MBR again sdb. I hope this makes it clearer, once you understand this it will be free flying, where if you have a dual boot such as windows and ubuntu to willl know how to reload the operating systems bootloader to the MBR=master boot record.

For example I have a laptop with XP and Karmic, I removed Karmic so I needed to just put the XP bootloader in the MBR with the XP install disc to get it to just boot XP.

---

### Post by alienprdkt on 2010-05-14
> **wilee-nilee said:**
> Grub2 automatically creates the grub.cfg file in the main bootable partition, but when asked where do you want grub it is talking about the grub that should only go to the MBR of the HD your installing to IE sda not sda1 or any other #. Now you have to know which drive your installing to, so if you had 2 HD's and you were installing to the second it would probably be called sdb so grub would only go to the MBR again sdb. I hope this makes it clearer, once you understand this it will be free flying, where if you have a dual boot such as windows and ubuntu to willl know how to reload the operating systems bootloader to the MBR=master boot record.

For example I have a laptop with XP and Karmic, I removed Karmic so I needed to just put the XP bootloader in the MBR with the XP install disc to get it to just boot XP.

Makes sense on why it didn't work now. Well I know for next time that it wants to know the location of the mbr. Thanks for clarifying that for me. I know exactly what you are talking about now, have done many MBR backups in my time, just not this past :lolflag: but where the MBR is located also has to match which drive is booting from the bios settings as well, correct?

---

### Post by wilee-nilee on 2010-05-14
> **alienprdkt said:**
> Makes sense on why it didn't work now. Well I know for next time that it wants to know the location of the mbr. Thanks for clarifying that for me. I know exactly what you are talking about now, have done many MBR backups in my time, just not this past :lolflag: but where the MBR is located also has to match which drive is booting from the bios settings as well, correct?

Basically yes, but there are different ways to set up grub, but the easiest is to make sure it is loaded just to the mbr of the HD the Ubuntu OS is going into. I am really mostly familiar with single HD setups, with multiple operating systems. So a person can install a windows os after one using grub, but to have grub be the boot, it just has to be reloaded into the MBR.

---

### Post by alienprdkt on 2010-05-14
> **wilee-nilee said:**
> Basically yes, but there are different ways to set up grub, but the easiest is to make sure it is loaded just to the mbr of the HD the Ubuntu OS is going into. I am really mostly familiar with single HD setups, with multiple operating systems. So a person can install a windows os after one using grub, but to have grub be the boot, it just has to be reloaded into the MBR.

Thanx! you helped me solved this issue.. now I have /boot on its own partition and booting correctly.

I have 8 hard drives! single boot system/

only multi-boot system I have is my laptop 

tri-boot windows vista (couldnt put xp onit due to hard drive driver issue) so Instead of vista I put apple osx leopard (hackintosh.org) now I rarely use windows been that way for the past 3 yrs. unix unix unix! & loving it! 

with a really nice bootloader with nice icons [http://chameleon.osx86.hu/articles/introducing-new-features-added-to-next-version-of-chameleon-part-1]("http://chameleon.osx86.hu/articles/introducing-new-features-added-to-next-version-of-chameleon-part-1")

Thanks again!

---

