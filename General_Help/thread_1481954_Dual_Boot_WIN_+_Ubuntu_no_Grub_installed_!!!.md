---
title: "Dual Boot /WIN + Ubuntu/ no Grub installed !!!"
date: 2010-05-13
forum: General Help
---

### Post by PingBomb on 2010-05-13
Hello
because i've no trust at VVin**** and i don't wanna modify my boot record here some solutions. (This solution work **only at Win XP**) (later will update this post for other versions (vista & 7) just need some more tests

1. install win at ur hdd.
2. Install ubuntu **9.xx/10.04** somewhere (**DO NOT INSTALL GRUB**)
3. Use this files

All files and folder must be copied in C:\ (**[COLOR=Black]MAKE BACKUP AT ORIGINAL BOOT.INI[/COLOR]**) MAKE CHANGES IF NEEDED in included Boot.ini file. 
at this line>>>  [operating systems] multi(0)disk(0)rdisk(0)partition(1)\.........

Second change must be made in 
ubuntu\install\boot\grub\menu.lst

LINE: kernel /ubuntu/install/boot/vmlinuz root=/**dev/[COLOR=Black]sda6[/COLOR]** ro quiet  (DEV/SDA1.2.3.4.5.6.7)

Then ur ready to reboot. 
For those that use:

Ubuntu 9.xx & Ubuntu 10.04
 
[http://www.4shared.com/dir/39651239/6c1166a0/linux.html](http://www.4shared.com/dir/39651239/6c1166a0/linux.html)

PS. Sry for my bad english.

---

### Post by gillesg06 on 2010-05-13
Sorry with my little experience with computers but I'm not sure what you mean

---

### Post by PingBomb on 2010-05-14
> **gillesg06 said:**
> Sorry with my little experience with computers but I'm not sure what you mean


I'm trying to say that if you already have installed windows xp, and the u want to install ubuntu (9.xx or 10.04) u don't need to install GRUB loader.
Just finish your ubuntu installation without grub install. Then use this files and after reboot u will have MENU that can choose what to run. Windows xp or Ubuntu.
This will prevend if you win box crash and you need to reinstall or your ubuntu box crash and u need to reinstall. No need to modify MBR records. :)

PS: My english is very bad so if some Moderator can make my post more readable let's do it :) 10x

---

### Post by lightstream on 2010-05-14
you have more faith in Windows' boot loader than GRUB?

---

### Post by obscurant1st on 2010-05-14
its good tip, but i am not gonna try it. Grub almost do  everythng. some time ago, i tried to boot mac from grub2, n it was successfull. :) i love grub2

---

### Post by PingBomb on 2010-05-14
> **lightstream said:**
> you have more faith in Windows' boot loader than GRUB?


sometimes yes, sometimes no :)

---

