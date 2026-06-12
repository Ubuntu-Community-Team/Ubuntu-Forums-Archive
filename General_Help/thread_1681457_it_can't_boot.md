---
title: "it can't boot"
date: 2011-02-04
forum: General Help
---

### Post by room206 on 2011-02-04
[IMG]http://img132.imageshack.us/img132/3347/04022011595.jpg[/IMG]
 
 
**[SIZE=5]what is the problem what can i do [/SIZE]**

---

### Post by Quackers on 2011-02-04
Welcome to UF :-)
What happens if you press enter when the top menu item is highlighted? Does it return to the grub menu?
Have you tried booting the recovery mode entry? What happens?

---

### Post by room206 on 2011-02-04
thankyou 
 
a lot of whit word end with 
(initramfs)

---

### Post by Quackers on 2011-02-04
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

