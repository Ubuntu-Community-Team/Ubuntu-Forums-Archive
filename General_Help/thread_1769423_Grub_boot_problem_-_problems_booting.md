---
title: "Grub boot problem - problems booting"
date: 2011-05-27
forum: General Help
---

### Post by BMR777 on 2011-05-27
Hello,

I recently installed Windows XP on my system that had Ubuntu on it.  I followed the instructions to restore the Grub bootloader so I could boot into Ubuntu, and they worked, sort of.

Whenever I boot, I get a grub prompt.  Typing configfile /boot/grub/grub.cfg brings me to the grub bootloader choice screen where things work like normal after that.

Basically, I want to know how I can get it so I don't have to type the command every time I boot up.  I already tried update-grub which updated grub.cfg but hasn't solved the issue.

Thanks!

---

### Post by Rubi1200 on 2011-05-28
Hi and welcome to the forums :-)

Please do the following so we can see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

