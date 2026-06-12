---
title: "GRUB Not Working. Please HELP!!!"
date: 2011-05-11
forum: General Help
---

### Post by Coasterfreakie on 2011-05-11
I installed Windows XP on my machine and loading everything in it. I then installed Ubuntu as a secondary installation. I have tried installing Ubuntu on the same hdd as XP as well as a secondary hdd. Neither installation will allow Ubuntu to load at startup. I tried reinstalling GRUB. I tried repairing the GRUB installation which only gave errors. As of right now I can only access XP and not Ubuntu. Please help.

---

### Post by LostFarmer on 2011-05-11
>  I tried repairing the GRUB installation which only gave errors  How, what errors ?
> Neither installation will allow Ubuntu to load at startup  ??  Do you get a grub menu ?  Have you used linux before and know basic commands ?

---

### Post by Coasterfreakie on 2011-05-12
Unfortunately I did not write the errors down but I followed all of these

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

tutorials to the tee and I still get no grub loader. It boots directly into xp. As for my Linux experience it is still somewhat limited to date but I understand command lines and the like. Any help is truly appreciated.

---

### Post by Quackers on 2011-05-12
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

