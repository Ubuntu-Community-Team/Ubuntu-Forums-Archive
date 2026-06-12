---
title: "Uninstalling Properley"
date: 2012-06-07
forum: General Help
---

### Post by pakakid on 2012-06-07
Hey guys, I currently have ubuntu on my laptop but due to lack of gaming support I decided to go back to windows 7. My question is what are the proper steps to install windows 7? If I load windows 7 on a usb stick and boot it from the windows screen, does the file have to be an ISO or can it be an exe? Thank you for anyones help

---

### Post by WorMzy on 2012-06-07
No idea about your Windows question, try asking on a Windows forum.

As for "uninstalling" Ubuntu, you can simply delete the partition that you installed it onto. You may as well delete the swap partition too (if you made one).

---

### Post by Shadius on 2012-06-07
I've only installed Windows from a .iso image and when you do, it asks if you want to format the entire disk for Windows or partition it. If you don't want Ubuntu anymore, you can just format the hard disk drive when you're installing Windows and you'll only have Windows. When installing Windows after Ubuntu, the Windows bootloader will take over the GRUB anyway. Hope that helps.

This link might help.

[Installing and Reinstalling Windows]("http://windows.microsoft.com/en-US/windows7/Installing-and-reinstalling-Windows-7")

---

### Post by pakakid on 2012-06-07
While trying to install it says windows 7 cant recognize my partitions, what did ubuntu do?

---

### Post by Shadius on 2012-06-07
> **pakakid said:**
> While trying to install it says windows 7 cant recognize my partitions, what did ubuntu do?

Windows cannot recognize Linux partitions like EXT4. Windows only sees FAT and NTFS.

---

