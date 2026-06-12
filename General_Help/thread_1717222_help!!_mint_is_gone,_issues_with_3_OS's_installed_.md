---
title: "help!! mint is gone, issues with 3 OS's installed on one computer"
date: 2011-03-29
forum: General Help
---

### Post by stber321 on 2011-03-29
i have a Toshiba satellite l505d-gs6000, it had a duel boot Linux mint and windows(although i have not used windows for over a year on my computer).

it had 4 partitions i shrunk my main windows partition again and made more space, i reformatted /dev/sda3 (windows restore) to ext4 and installed openSUSE, i used the same swap partition. openSUSE removed GNU GRUB and now i can only boot into windows and openSUSE, the partition that mint is installed on is still there (/dev/sda6) but i cannot boot into it. also wireless networking does not work on openSUSE. please help.

---

### Post by wilee-nilee on 2011-03-29
openSUSE is grub legacy mint is grub2 follow this link to reload grub2 to the mbr, grub2 will see all the OS's. Load the sda6 and sda=mbr, if sda6 is mint, use a ubuntu cd with grub2 or the mint cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You could add mint to the menu.list in grub-legacy, in openSUSE, but it hardly seems worth it when grub2 will do it all from mint.

---

### Post by stber321 on 2011-03-29
> **wilee-nilee said:**
> openSUSE is grub legacy mint is grub2 follow this link to reload grub2 to the mbr, grub2 will see all the OS's. Load the sda6 and sda=mbr, if sda6 is mint, use a ubuntu cd with grub2 or the mint cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You could add mint to the menu.list in grub-legacy, in openSUSE, but it hardly seems worth it when grub2 will do it all from mint.



thank you verry much you have helped me get everything under control (do you know how where to get drivers for my wierless card. Ubuntu based distros so far are the only ones that work, i have tried Debian, fedora, blang, gentoo and freeBSD(obviously not really a GNU/Linux distro) and iwconfig tells me i have no wireless interfaces on all these distros. i have Debian running on another laptop with a broken screen, and i love it whenever i can find the VGA cable.

---

### Post by wilee-nilee on 2011-03-29
> **stber321 said:**
> thank you verry much you have helped me get everything under control (do you know how where to get drivers for my wierless card. Ubuntu based distros so far are the only ones that work, i have tried Debian, fedora, blang, gentoo and freeBSD(obviously not really a GNU/Linux distro) and iwconfig tells me i have no wireless interfaces on all these distros. i have Debian running on another laptop with a broken screen, and i love it whenever i can find the VGA cable.

Not sure about wireless drivers. Start a new thread and posting the actual card would be a good start probably. Use the thread header as a accurate descriptive.

---

