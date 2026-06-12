---
title: "Grub2 detects NTFS partition as Windows OS."
date: 2012-08-10
forum: General Help
---

### Post by omelette on 2012-08-10
Grub2 detects a newly-created partition (sda1) as a Windows OS, creating a menu entry for same.  Its boot-flag isn't set and is only used to store stuff. Re-running 'grub-install --root-directory=/mnt/ /dev/sda' from the LiveCD didn't help.

Does anyone have a remedy?

---

### Post by Cavsfan on 2012-08-10
Used Gparted  and select that partition and click on it and then manage flags and uncheck Boot.
Then go to the real windows partition, click on it and then manage flags and then check Boot.
That should fix it.
If you can get into your Ubuntu, enter **sudo grub-install /dev/sda**

Did that help any?

I have a custom grub menu from the How to in my sig. and I only see what I have set up.
One time I unchecked the boot flag on my windows 7 partition and it worked fine but, would not go into sleep mode. I had to add the check back to boot before it would sleep.

---

### Post by oldfred on 2012-08-10
Grub normally only creates boot entries for those partitions with boot files. For XP it is ntldr & boot.ini and Vista/7 bootmgr and the BCD. Do you have boot files in your NTFS partition? Grub does not use boot flag, but Windows has to have boot flag to boot directly with its MBR boot loader, or make boot repairs.

Or you can hide the entry.
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)

---

### Post by omelette on 2012-08-11
Although I don't have any flavour of Windows on the hard-drive, as **oldfred** suggested, I do have 'boot.ini' and 'ntldr' - no doubt left over from a copy & paste from my old XP installation!  So, sorted!

Thanks guys. :)

---

### Post by oldfred on 2012-08-11
Glad that worked.

You can change to solved.

Also you should have a Windows install or Windows repairCD, so you can run chkdsk periodically or whenever there are issues. You cannot do chkdsk from Linux.

---

