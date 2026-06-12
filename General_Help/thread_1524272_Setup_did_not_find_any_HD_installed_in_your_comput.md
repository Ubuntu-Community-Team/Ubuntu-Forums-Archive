---
title: "Setup did not find any HD installed in your computer"
date: 2010-07-05
forum: General Help
---

### Post by COKEDUDE on 2010-07-05
Could anyone explain why I am getting this message when trying to install XP.
"Setup did not find any HD installed in your computer." I have Ubuntu installed on another partition so it makes no sense that XP doesn't recognize my HD.

---

### Post by 4Orbs on 2010-07-05
Windows is blind to Linux partitions. It's better to install Windows before any others when creating a dual-boot setup. I suggest booting into your Ubuntu live cd, and when you get to the livecd desktop open gparted from the system menu and create a primary partition for windows, format it to ntfs or fat32, turn on the boot flag for it. Exit the live cd and then boot into your Windows install disk. If the Windows disk now can see your hard drive, tell it to quick-format (yes, again)  your new partition as ntfs or fat32 and proceed with the install. Once Windows is installed you will no longer have the grub boot menu, so you'll need to re-install grub by using the Ubuntu live cd. There are instructions somewhere else on these forums for doing that... sorry I don't have the link at this moment.

---

### Post by COKEDUDE on 2010-07-05
> **4Orbs said:**
> Windows is blind to Linux partitions. It's better to install Windows before any others when creating a dual-boot setup. I suggest booting into your Ubuntu live cd, and when you get to the livecd desktop open gparted from the system menu and create a primary partition for windows, format it to ntfs or fat32, turn on the boot flag for it. Exit the live cd and then boot into your Windows install disk. If the Windows disk now can see your hard drive, tell it to quick-format (yes, again)  your new partition as ntfs or fat32 and proceed with the install. Once Windows is installed you will no longer have the grub boot menu, so you'll need to re-install grub by using the Ubuntu live cd. There are instructions somewhere else on these forums for doing that... sorry I don't have the link at this moment.

Ok thx for explaining that. I'll test it out. I have the link. I've messed up my grub several times so I keep that link bookmarked :). 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

