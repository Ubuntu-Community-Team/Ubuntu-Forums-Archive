---
title: "After reinstalling window xp can't get ubuntu option on the boot."
date: 2011-01-10
forum: General Help
---

### Post by rahul1975 on 2011-01-10
I have windows 7 and ubuntu 10.04 lts on the same hard disk, having dual boot system. My problem is that after formatting c: drive and installing windows xp the ubuntu option does not appear and windows xp starts directly without any options of dual boot.So how to get the option of ubuntu again to start ubuntu.please guide me as i am new to ubuntu.

---

### Post by Quackers on 2011-01-10
You will need to re-install grub to the mbr of the drive.
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sakuramboo on 2011-01-10
Windows installed their own bootloader, replacing grub2. You need to reinstall Grub2.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

