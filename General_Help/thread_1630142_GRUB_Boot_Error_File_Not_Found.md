---
title: "GRUB Boot Error: File Not Found"
date: 2010-11-24
forum: General Help
---

### Post by Linux100 on 2010-11-24
Hello. I have a problem. I have tried to install another version of Linux, and then I rebooted. Everything was fine until I was given a command line with an error saying "File Not Found!". How do I fix it?

---

### Post by Quackers on 2010-11-24
Welcome to UF :-)
Please boot from the Ubuntu Live cd and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

