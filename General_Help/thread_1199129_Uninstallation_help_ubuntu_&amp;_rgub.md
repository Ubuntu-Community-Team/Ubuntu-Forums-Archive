---
title: "Uninstallation help ubuntu &amp; rgub"
date: 2009-06-28
forum: General Help
---

### Post by mraza08 on 2009-06-28
hi all !
      i am new to the site here and currently using ubuntu live CD to post this thread so please it will be a great thing if somebody can give a quick help. i had installed XP on my desktop. i wanted to know about linux and i installed it via boot from CD at the the startup of computer. now whenever my computer is opening there is a message something like RGUB loading and error 17.. i can't pass this windos untill to boot windows or anything...i am trying all the day. please i just want to remove ubuntu and rgub from my system, it is installed on seprate drive inside computer. i will install it later via windows. please help me

---

### Post by K.Y.A on 2009-06-28
If you are in  Ubuntu live cd, click System, Administration, partition editor. Select your drive in the upper corner of the partition window, and then find what partition is NOT NTFS. Format all the partitions that are NOT NTFS and then make your NTFS partition larger. Click apply, and then reboot with the windows xp cd. You will then have to either reinstall XP or reinstall its bootloader, since grub overwrites it. Google how to reinstall xp bootloader and write down instructions. Good luck.


EDIT: Error 17 is commonly caused by a failing hard drive. First the first few sectors of the drive (~512kb) get corrupted, causing error 17, but even after that is fixed, the errors will spread until the drive dies. It's just natural hard drive death, it happens to everyone. Mine just did the same thing. :( I had to send the drive to seagate for replacement. If I were you, I would backup your data now. It could be months or days until the drive dies.

---

### Post by xpod on 2009-06-28
If you have an XP cd then load that up and use the recovery console to execute the fixmbr command.Then just delete the Ubuntu partition from within the Windows disk management console.
If you dont have an XP cd then get your hands on a 98 bootdisk or similar and use that to fix your MBR.

---

