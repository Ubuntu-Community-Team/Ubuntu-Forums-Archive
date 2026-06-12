---
title: "PLEASE HELP-Grub booting"
date: 2010-12-17
forum: General Help
---

### Post by Saggat on 2010-12-17
Now i have two different OS in different partitions and i want to doble boot with grub.
When i start my pc i get the GRUB TERMINAL:
grub>

someone knows how to boot? i googled it but i dont know how to do it.

---

### Post by Rodney9 on 2010-12-17
If only the word "Grub" appears at the top of the screen without a prompt (access to the command line) or menu, refer to the [Reinstalling from LiveCD section]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

---

### Post by Saggat on 2010-12-17
> **Rodney9 said:**
> If only the word "Grub" appears at the top of the screen without a prompt (access to the command line) or menu, refer to the [Reinstalling from LiveCD section]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

No, i mean, i can see the command prompt.

---

### Post by oldfred on 2010-12-17
I think that is the grub prompt and not the Ubuntu prompt. Can you manually boot with these commands? Or else you will have to reinstall grub from a liveCD.

grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
Or:
Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,1)/vmlinuz root=/dev/sdb1
sh:grub>initrd (hd1,1)/initrd.img
sh:grub>boot

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Saggat on 2010-12-17
Wow,thats difficult, i try to add a entry with easybcd but when i select ubuntu i get the grub> prompt and i really dont know what to do there.
I TRY configfile (hd0,1)/boot/grub/grub.cfg AND IT WORKED
YOU´RE MY HERO! Thank you!

---

### Post by oldfred on 2010-12-17
I do not know easyBCD, but I thought it was supposed to work completely on its own to boot.

I like grub2 and use it. If you want grub2 to control booting then from your Ubuntu install you have to reinstall grub2 to the MBR so it controls the booting. 

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

