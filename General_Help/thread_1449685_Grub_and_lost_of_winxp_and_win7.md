---
title: "Grub and lost of winxp and win7"
date: 2010-04-08
forum: General Help
---

### Post by loboaureo on 2010-04-08
Hi, i need to be able of start my computer in ubuntu, winxp, and win7.

I install an xp, and a win7 and after that an ubuntu. The problem is with the grub install, that only appears the ubuntu.

My hd are organized in the next form:

-SDA (fat32, 750gb, shared data between wins and ubuntu)
-SDB (ntfs, 500gb, big files and data for wins)
-SDC1 (ntfs, 50gb, Winxp)
-SDC2 (ntfs, 110gb, win7)
-SDD (swap, ext4,160gb for ubuntu)

¿how could i fix it?, if i need to reinstall the xp or the 7, there will be no problem, but in the ubuntu i have son configs that i dont want to lost.

Thanks in advanced and sorry for my bad english.

---

### Post by aeiah on 2010-04-08
seems grub only looked on SDD for operating systems so it didnt see windows. you could try restoring grub, or manually adding the grub entries

---

### Post by loboaureo on 2010-04-08
i try with "sudo update-grub" but nothing is detected.

So i supose that manually is the option. I open the file /boot/grub/grub.conf, but dont know what to add (and where) to make it works.

---

### Post by oldfred on 2010-04-08
You are not to edit grub.cfg. It gets updated on every new kernel and some other times. And everytime you run sudo update-grub.

Lets see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

