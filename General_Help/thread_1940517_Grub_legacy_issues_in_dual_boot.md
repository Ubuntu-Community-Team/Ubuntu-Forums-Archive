---
title: "Grub legacy issues in dual boot"
date: 2012-03-13
forum: General Help
---

### Post by kschumake83 on 2012-03-13
ok so long story short i have a lenovo b570 with the buggy uefi bios and i am trying to get a dual boot going.  my system is running ubuntu 11.10 and windows 7.  i installed windows 7 and then ubuntu but it wouldn't see the grub 2 menu it would just boot straight to windows. so i used a grub boot disk that sees both windows and ubuntu, and booted up ubuntu. i tried installing all the updates to get to the newer kernel and that did not help. so then i booted to ubuntu again and installed grub legacy. now i see grub when i start the computer but i dont see windows. when i run the update-grub it doesnt show windows just ubuntu but if i us os-prober it shows /dev/sda1:Windows 7 (loader):Windows:chain, so obviously it knows windows is there. any help getting this going would be appreciated.

solved for my purposes

---

### Post by YannBuntu on 2012-03-14
Hello,
please could you indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") ?  (don't try the Recommended repair at the moment)

---

### Post by kschumake83 on 2012-03-14
i actually got it straightened out this morning with a reinstall of everything and tripple booting with linux mint. linux mint uses grub legacy from the beginning and is easier to config (and i like the cinnamon interface sometimes anyways) so i just removed grub from ubuntu and i let mint take care of the booting and all works well.

---

### Post by YannBuntu on 2012-03-14
ok. Please could you add [Abandoned] in the title then ?

---

