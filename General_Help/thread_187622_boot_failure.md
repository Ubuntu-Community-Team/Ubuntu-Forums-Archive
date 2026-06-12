---
title: "boot failure"
date: 2006-06-03
forum: General Help
---

### Post by bootwoes on 2006-06-03
I've taken the plunge and installed ubuntu. my initial attempt to dual boot destroyed my xp, so i installed it on a seperate SATA drive by itself.

everything works fine when there is only one drive. If I try to hook up my other SATA drives, it fails to boot. it seems to get confused and cant find anything. 

unplug other drives, and its fine again.

any help will be much appreciated
thanks

jon

---

### Post by Nathaniel on 2006-06-03
This is exactly why I suggested that Dapper isn't ready for release at all.

Bugs like these are extremly severe. It seems like the installer can't really handle the dynamic nature of SATA-drives.

First off, it simply installs GRUB on very first harddrive. It doesn't matter if that's actually the drive I boot from, it gets installed there anyway (and it doesn't even ask...). Second, it seems that the GRUB notation "(hd0)" and the /dev notation "/dev/sdc" don't always match. Thus, both the installer and GRUB gets confused and the system shits itself at boot.

Try booting in safe-mode, and manually rewrite /boot/grub/menu.lst so that it points to the correct harddrives. It may take some trial and error, but it should work eventually. And beware of upgrading the kernel. If yo do, the grub menu-file will get dynamically overwritten.

---

### Post by bootwoes on 2006-06-03
hmmm.. i've gotten a little further.
for some reason it decided it would boot from SATA3 instead of SATA1.
so i swapped my ubuntu drive to SATA3 and the other to SATA4 and woila.. it booted.

---

### Post by Nathaniel on 2006-06-03
Precisely :>

My BIOS boots the drives as sda=storage1, sdb=storage2 and sdc=main-drive, and that's the way they show up when I boot into linux. However, GRUB thinks these drives are (hd0)=main-drive, (hd1)=storage1 and (hd2)=storage2 (because I choose to boot that particular drive in the BIOS settings). Therefor, the Ubuntu installer writes GRUB to what IT believes is the main-drive (ie. (hd2)) and lets GRUB sit there and look around for the kernel on what is really my /dev/sda.

Sucks, that a blatant logical mistake in the installer would seep through into what is the big Ubuntu flagship :(

---

