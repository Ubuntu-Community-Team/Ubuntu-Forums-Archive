---
title: "How do I remove Windows 7 installation?"
date: 2011-03-06
forum: General Help
---

### Post by andrefiker on 2011-03-06
I want to keep only ubuntu OS and remove installed windows 7, can someone plz help?

Tks!

---

### Post by zenwalker on 2011-03-06
Just format the win 7 drive. And if you have boot loader like Grub, just boot into Ubuntu and edit the grub conf file to remove win 7 entry.

---

### Post by andrefiker on 2011-03-06
> **zenwalker said:**
> Just format the win 7 drive. And if you have boot loader like Grub, just boot into Ubuntu and edit the grub conf file to remove win 7 entry.


How do I format the drive? sorry, I am really new to this. Used to Windows but first day with Ubuntu. I`ll search for grub though seems good tks!

---

### Post by zenwalker on 2011-03-07
This should help you [http://ubuntuforums.org/showthread.php?t=554722](http://ubuntuforums.org/showthread.php?t=554722)

---

### Post by Quackers on 2011-03-07
In gparted just delete the Windows partitions (making sure you don't delete the recovery partition - if you mean to keep it).
Then run ```
sudo update-grub
``` in the terminal to get rid of the Windows entry.

---

### Post by xwhyz on 2011-03-07
i to need to edit the grub menue.
i had ro reinstall unbuntu and now have 2 entries for unbuntu

i tried 

sudo update-grub

which lists the entries but i cant seem to edit them.


found this which is what i needed [crub customiser]("http://ubuntuforums.org/showthread.php?t=1664134&highlight=configure+grub")

---

