---
title: "GRUB configuration"
date: 2010-01-17
forum: General Help
---

### Post by Luc 284 on 2010-01-17
I have recently installed Ubuntu Karmic on my laptop, which also has Windows 7. It now has GRUB, and I have been able to modify some settings via the GRUB command line.

However, these changes are not permanent; they are reset the next time I load GRUB. I have seen many people trying to configure GRUB who have been pointed towards /boot/grub/menu.lst. Figuring that this would help me solve my problem (and I expect it would) I went to edit that file... and discovered that it did not exist. I am certain that I am using GRUB, not some other bootloader.

Is there another possible way to configure GRUB, or somewhere else I might look for this file?

Thanks,
Luc

---

### Post by garvinrick4 on 2010-01-17
You are using grub2 not grub legacy so you do not have a menu lst.
I am on a Live CD so do not have quick access to Bookmarks so Google
grub2 if you need a link. Have a nice day.

---

### Post by dlhoppe on 2010-01-17
For Grub2, edit the /etc/default/grub file to change settings, then run update-grub to apply. 
 
I just learned this today for some issues I'm having. Hope this helps you.

---

### Post by Luc 284 on 2010-01-17
[COLOR=DimGray]Actually, I had tried editing the /etc/default/grub file, since I figured it might be relevant. Thanks! I now know that I have the right file. I think I will be able to figure it out now[/COLOR].

Edit:

Unfortunately, with my meddling around before posting here, I think I somehow managed to install the legacy version of GRUB, or at least whatever version is in the universe called "grub". Now, whenever I try to load Ubuntu (including in recovery mode), it tells me the environment block size is too small. However, I still don't seem to have a /boot/grub/menu.lst file. Now running off of the live CD, how can I fix this?

---

### Post by Luc 284 on 2010-01-18
When I boot up my system, it shows GRUB version 1.97. However, I can find files on my system that appear to be for older versions of GRUB. Any ideas on how I can fix this besides a complete reinstall?

---

