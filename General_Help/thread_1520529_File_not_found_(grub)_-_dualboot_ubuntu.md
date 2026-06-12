---
title: "File not found (grub) - dualboot ubuntu"
date: 2010-06-29
forum: General Help
---

### Post by rXp on 2010-06-29
Hello,

I have the 10.04 ubuntu installed and today I installed a distrib based on the 8.10 version of ubuntu.
The installation seems to go well but after the reboot I could only boot on the 8.10.
For the other the error is : "Error #15 File not found".
I tried to reinstall the grub ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) but no changes.
I checked the 10.04 and it is not corrupted or anything...
What should I do ?

Best regards,

rXp>!<

---

### Post by ajgreeny on 2010-06-29
Not sure, but I think that may be because 8.10 is not properly ext4 enabled, and perhaps the grub menu.lst file does not contain the correct info for an ext4 install, ie your 10.04.

Using your 10.04 live CD restore the grub from that, (grub2), then reboot and you should go to 10.04, from where the command ```
sudo update-grub
``` should add 8.10 to your grub2 menu

See section 13 on [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by rXp on 2010-06-30
> **ajgreeny said:**
> Not sure, but I think that may be because 8.10 is not properly ext4 enabled, and perhaps the grub menu.lst file does not contain the correct info for an ext4 install, ie your 10.04.

Using your 10.04 live CD restore the grub from that, (grub2), then reboot and you should go to 10.04, from where the command ```
sudo update-grub
``` should add 8.10 to your grub2 menu

See section 13 on [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Thank you a lot it worked ! :)

---

