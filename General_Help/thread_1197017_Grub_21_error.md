---
title: "Grub 21 error"
date: 2009-06-25
forum: General Help
---

### Post by xc_runner on 2009-06-25
hi, 
i'll start by saying i'm a newbie with linux, but i do tri boot Xp/Windows 7/ and ubuntu on my *desktop*. 
so i decided to install Ubuntu on my 8 gig flash drive and experiment with booting it via USB on my *laptop *which has Vista Business installed on it.  i formatted the flash drive, insterted the Ubuntu cd, restarted my computer, and did guided installation, installing it to the flash drive.  it worked as intended. but when i restarted and booted ubuntu from the flash drive it failed to load and dropped to a shell prompt.

when i removed the flash drive and rebooted , the computer tried to load GRUB instead of MBR, giving me the GRUB 21 error.  so i need the flash drive plugged into my computer to boot Vista.  i googled it and tried some suggestions;
[MBRFix.exe]("http://www.sysint.no/en/Download.aspx") tells me i have the wrong verion when run in the cmd prompt as an admin in Vista
and when i tried to run linux live from the ubuntu cd, to use the suggestion from the [pendrive linux page]("http://www.pendrivelinux.com/grub-error-21-after-full-install-to-usb-hard-drive/"), it gave me an error and told me to reboot.  I've run it Live before so i'm not sure whats up there...

there's no urgency on this, i'd just like to get it fixed.  if i have to uninstall ubuntu on the flash drive in, i'm ok with that if it'll restore the MBR.  and i would need advice on how to do that as i already tried that with the Ubuntu CD as well, resulting in the same error message..  and if anyone needs more details just ask and i'll try to give them

thanks in advance

---

### Post by 73ckn797 on 2009-06-25
You could restore the mbr on the main system using the XP CD and going into recovery mode and entering "fixmbr". 

If you look around you may find how to install grub to the pendrive to boot off of it. I have not tried what you are doing but have seen this issue before in the forums

---

### Post by Megrimn on 2009-06-25
Error 21 would mean that GRUB cannot find the disk.  So GRUB is searching for the usb drive becuase it is in the bootlist.

I think that some how you must have GRUB installed on your HDD, because GRUB wouldn't come up if it was installed on the USB drive.  I think you will need to uninstall GRUB from the HDD and then probably re-install Ubuntu on the USB drive so that it includes GRUB.

---

### Post by jimv on 2009-06-25
This should get your Windows installations back up and running:

[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

And also, when installing to a thumbdrive, you want to make sure that on the final screen before the actual installation starts that you click the Advanced button and make sure that the boot loader gets installed onto the thumbdrive, not your regular HD.

---

### Post by Megrimn on 2009-06-25
> **jimv said:**
> This should get your Windows installations back up and running:

[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

And also, when installing to a thumbdrive, you want to make sure that on the final screen before the actual installation starts that you click the Advanced button and make sure that the boot loader gets installed onto the thumbdrive, not your regular HD.

What he said.  Though you think that you would be able to repair mbr from recovery mode...

---

### Post by xc_runner on 2009-06-25
i have a windows xp and windows 7 instillation cds... would it work to use the xp disc for example to restore the Vista MBR?...

also in the link, this might sound nooby.. but how would i "change [my] directory to boot" while in the recovery prompt?


my laptop has a recovery disc creator. is that what i would want to do?  burn a recovery disc and reboot and use that?  or is that something different..

---

### Post by lindsay7 on 2009-06-26
You can download a vista recovery disk here,

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

