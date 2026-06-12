---
title: "Dual boot problem xp and ubuntu"
date: 2010-11-20
forum: General Help
---

### Post by aksh1t on 2010-11-20
I just installed win xp in my 80 gb hdd in a 38 gb partition, and set it up with all software and things. Then i installed ubuntu 10.10 with the advanced partitioning options. i gave another 38 gb partition to /, 1.5 gb to /boot and 2 gb as swap space. i also made the windows partition to mount at /windows but forgot to make it bootable. now i restarted my pc and instead of asking me the os to boot, it directly starts ubuntu. i also made the windows partition bootable inside ubuntu by using disk utility but still the problem. And i cant find any menu.lst file in my boot/grub...

---

### Post by Quackers on 2010-11-20
Welcome to UF :-)
Having installed 10.10 you won't find a usable grub menu.list file as 10.10 now uses grub2, which has different configuration files. It may be that the Windows bootloader needs fixing.
Please go to the site below and download the boot script to your DESKTOP then open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

