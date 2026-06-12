---
title: "I've just killed my laptop? no grub, no OS, only bios"
date: 2011-01-20
forum: General Help
---

### Post by OpenTu on 2011-01-20
Unplug any usb device 

put the live cd  in bios Dell Screen Press F12 then u will see a menu
Choose Boot CD/Rom 

..

---

### Post by Quackers on 2011-01-20
If you've deleted sda1 and your Windows installation was Win 7 you may have lost a couple of Windows boot files.
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

