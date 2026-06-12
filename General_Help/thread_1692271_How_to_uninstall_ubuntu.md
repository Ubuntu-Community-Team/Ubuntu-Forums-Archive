---
title: "How to uninstall ubuntu"
date: 2011-02-21
forum: General Help
---

### Post by insanity99 on 2011-02-21
Don't worry, I'm not leaving ubuntu, just transferring to a new pc. How to I safely remove it? I am duel booting with windows.


Will this also free up my 3 partitions that I made while installing ubuntu?

Thanks

---

### Post by megabuffen on 2011-02-21
As far as I know, you can just remove the partitions that Ubuntu has been installed on. The GRUB boot loader should still boot Windows for you. However, I found this article which describes how to use a Windows XP installation CD to restore the default Windows boot loader. It also details the use of the Windows disk manager. That way, you will no longer have to choose which OS to boot.

[http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

---

### Post by insanity99 on 2011-02-21
ah damn. i removed the partitions in windows but now when i try to boot up i get 

error: unknown file system
grub rescue


ahhhh noooo

---

### Post by Hippytaff on 2011-02-21
you should be able to restore the mbr withthe windows boot loader from a windows installation disc

---

### Post by insanity99 on 2011-02-21
i cant access it, i keep my backup cd on c: drive, stupid i know.

---

### Post by Hippytaff on 2011-02-21
If you can boot from liveusb you should be able to access your windows partition and get the file, burn it to disc.

---

### Post by insanity99 on 2011-02-21
i have knoppix. someone said i can reinstall grub to solve the issue. i have it booted up

---

### Post by Hippytaff on 2011-02-21
That should do it.

---

### Post by insanity99 on 2011-02-21
ok im on knoppix, how do i install grub?

---

### Post by Hippytaff on 2011-02-21
haha...sorry, no idea. I've never tried before so I wouldn't like to hazzard a guess. Maybe someone with a bit more experience of doing this will chime in, but I'd start by googling :-)

---

### Post by insanity99 on 2011-02-21
man this is stressing me out. dont know how to do it.

---

### Post by wiggly81 on 2011-02-21
sorry if outside links are not allowed but i have found somthing that may help..

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

hope it helps and hope i dont get wrong lol

---

### Post by Hippytaff on 2011-02-21
Sorry, I didn't mean to abandon you there, just at work...this might also be worth a look
[http://www.linuxforums.org/forum/installation/53739-install-grub-through-knoppix.html](http://www.linuxforums.org/forum/installation/53739-install-grub-through-knoppix.html)

---

### Post by insanity99 on 2011-02-21
It's ok.

For now I have had to install ubuntu again. It means all my hard work was for nothing because ubuntu is still on this HDR but I can get too windows again at least

---

