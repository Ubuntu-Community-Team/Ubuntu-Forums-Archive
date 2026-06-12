---
title: "GRUB doesn't show Windows 7..."
date: 2012-05-07
forum: General Help
---

### Post by EpicFlyingCoffee on 2012-05-07
Hello everyone,
I'm not to sure if this topic goes here...but I guess I'll put it in General Help.

Okay, so when I installed Ubuntu (Precise) two days ago, it asked me where to put GRUB bootloader. Not knowing where to put it, I put it where the Windows boot loader used to reside (Which was in the special 100mb partition). After installing, I rebooted to find the new boot menu. I selected "Windows 7 (loader)", but it just went back to GRUB (When booting to Ubuntu, it works fine). 
I made the assumption that I replaced the Windows loader so it just loops back around to GRUB. So, I then found out that I needed to put a custom entry in the Grub.d folder. I did that, and updated grub, but when I boot to my entry (That boots directly to the partition), the Windows DOS pops up and says: 
MBR damaged. Press Alt+Ctrl+Del to reboot.
I believe that there is no boot loader on the Windows partition and that is what is causing the problem. 
How can I fix this?:confused:

---

### Post by searchfgold6789 on 2012-05-07
Grub should have been installed on the **disk**, not the **partition**. If you try to install grub on a partition, then you will run into problems.
  Repair your system using this guide: [URL="https://help.ubuntu.com/community/Boot-Repair"]http://josephhall.org/grub_install_hda1.html
[/URL]

---

### Post by kc1di on 2012-05-07
Hi I think it's fixable. 

put in your windows 7 disc.  do the mbr fix from that then

following the instructions on this page to reinstall grub
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

you may also want to look here:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by EpicFlyingCoffee on 2012-05-07
Wow, thanks for the quick replies!
Rebooting now...

---

### Post by EpicFlyingCoffee on 2012-05-07
So I tried the Boot-Repair thing and...
Ehe...Well, it DID work (For Ubuntu at least). Until I messed it up.
So, I had to run it again on the LiveCD and it works fine except...
I still can't get to Windows. It keeps looping me back to GRUB when I try to use the "Windows 7 (loader)" command. I tried the direct one I made before and saw something along the lines of this:

Windows boot manager is damaged. Please insert the windows 7 disc, reboot, and click "Repair"

Do I need the disc, or can I just use Boot-Repair to "Restore the MBR"?

(Ugh. Why can't Windows and Linux just get along?!?!  ](*,))

---

### Post by searchfgold6789 on 2012-05-07
I think you need the disk, but try kc1di's suggestion.

---

### Post by wilee-nilee on 2012-05-07
You will have to clean up that windows boot partition to get in shape, so download this link extract it to the desktop and run the command and post the results.txt that appears to the thread so we can see the damage, not a hard fix generally.

Do you have a Windows recovery or install disc in case needed?

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
 sudo bash ~/Desktop/bootinfoscript
```

---

### Post by kc1di on 2012-05-07
> **EpicFlyingCoffee said:**
> So I tried the Boot-Repair thing and...
Ehe...Well, it DID work (For Ubuntu at least). Until I messed it up.
So, I had to run it again on the LiveCD and it works fine except...
I still can't get to Windows. It keeps looping me back to GRUB when I try to use the "Windows 7 (loader)" command. I tried the direct one I made before and saw something along the lines of this:

Windows boot manager is damaged. Please insert the windows 7 disc, reboot, and click "Repair"

Do I need the disc, or can I just use Boot-Repair to "Restore the MBR"?

(Ugh. Why can't Windows and Linux just get along?!?!  ](*,))

Yes you need the windows disc.

---

### Post by oldfred on 2012-05-07
Boot script as suggested by wilee-nilee would let us confirm if you have grub2's boot loader in the NTFS partition boot sector (PBR). NTFS have to have NTFS info in the PBR.

So many were making the error the author of the boot script posted this. NTFS keeps one backup of the PBR and you can restore the backup if you only wrote to it once.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by wilee-nilee on 2012-05-07
Darn sourceforge site is down right now oldfred, just when you need them lol. :)

Had not see YannBuntu's thread before nice instructions.

---

### Post by EpicFlyingCoffee on 2012-05-08
Wow. Thank you everyone. 
I wound up using YannBuntu's thread and it works fine. Both OSes boot up normally and I didn't even need to reinstall GRUB! I just updated it and it works.
Thanks so much!!!!!!!!!!  :-\"

---

### Post by wilee-nilee on 2012-05-08
> **EpicFlyingCoffee said:**
> Wow. Thank you everyone. 
I wound up using YannBuntu's thread and it works fine. Both OSes boot up normally and I didn't even need to reinstall GRUB! I just updated it and it works.
Thanks so much!!!!!!!!!!  :-\"

Cool that bootrepair tool is a nice one, glad your all set. :)

---

