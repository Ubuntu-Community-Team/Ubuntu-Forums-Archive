---
title: "dual boot help!!"
date: 2010-06-25
forum: General Help
---

### Post by ddeleon4 on 2010-06-25
ok i have had Ubuntu for almost a month now and I'm loving it. but i have ubuntu in 1 hard drive and XP in another and I am getting annoyed that when i start my pc i have to go the the startup menu and change the order in which this start to select between ubuntu and xp. i have searched and know that this would have been fix during the initial install but at that time i didn't have the hard drive which contained my XP installed, is there anyways of fixing this now without uninstalling and reinstalling the either OS (i have done a lot of stuff to personalize both and i don't feel like redoing everything)? i have already searched about this but all that i get pertains to the initial install.

---

### Post by oldfred on 2010-06-25
Welcome to the forums.

Since both were standalone drives there may be confusion on who is first. But often all you need to do in Ubuntu is:

sudo update-grub

It should add the windows entry to the grub menu and let you boot it on next reboot.

---

### Post by ajgreeny on 2010-06-25
As you disconnected the Win XP disk when you installed ubuntu the grub menu will not have added the Win XP to the menu.  It should have done so in any updates to the kernel, if you have done those, so it should now have ubuntu and WinXP in the menu.  If not, just run **sudo update-grub** as oldfred said.

I assume you are at the moment having to change the boot order when you boot up the machine, either to go straight to Win XP when that disk is set as first boot device, or to grub, which should now show both OSs when the second (Ubuntu) disk is set as first boot device.

If that is where you are at present, simply go into the BIOS (not the boot menu) at boot up and set the second (Ubuntu) disk to be the  first boot device permanently, which should then take you to grub by default.  You could also just boot to Ubuntu and then run ```
sudo grub-install /dev/sda
``` to replace the windows MBR bootloader with grub but this second method will remove the windows bootloader so if you should ever choose to completely remove Ubuntu, you will not be able to boot to Win XP without restoring the Win XP bootloader..

---

