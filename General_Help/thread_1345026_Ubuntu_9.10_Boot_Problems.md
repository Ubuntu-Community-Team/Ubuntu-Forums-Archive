---
title: "Ubuntu 9.10 Boot Problems"
date: 2009-12-03
forum: General Help
---

### Post by poder39 on 2009-12-03
I installed Ubuntu 9.10 yesterday, using the web installer, and everything worked fine. When I would boot, it would give me the option to boot to either Windows XP or Ubuntu. This morning though, it doesn't give me the option and it just automatically boots into Windows XP. I'm very new to Ubuntu, so any help would be awesome!

---

### Post by RedMaster on 2009-12-03
Are you sure you have installed it right? Maybe you forgot to install the boot loader GRUB :)

PS:
Give us more information :) 
I'm sure there are people over here who can help you! :)

---

### Post by oldfred on 2009-12-03
When you said web install did you mean wubi install inside windows or a full install for dual booting using a minimal install and downloading everything from the web?

---

### Post by StuartN on 2009-12-03
It would do no harm to restore Grub [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) but be sure to use a version of the Live CD with the same version of Grub as you have.

---

### Post by poder39 on 2009-12-04
I believe that I used to Wubi installer inside windows. It was the version that I didn't have to download and then burn the .iso file. The ubuntu website says that Grub2 should have been installed with Ubuntu 9.10, but I can't find it or get it to open/work. I'm really new to this kind of stuff, but I know that I really liked it when it worked, so any help would be awesome. If there are any specific questions that could help, feel free to try to IM me on yahoo (poder39) or AIM (sven423942)

---

### Post by StuartN on 2009-12-04
> **poder39 said:**
> I believe that I used to Wubi installer inside windows.

If you installed inside Windows then you have the Windows boot loader and will need to edit BOOT.INI for Windows up to XP, or use BCDEDIT.EXE for Vista or Windows 7. This will involve some reference to wubildr and wubildr.mbr in the folder \Ubuntu\winboot\, possibly as simple as adding the line **C:\wubildr.mdr = "Ubuntu"** to BOOT.INI.

If you did a proper install then you would have a separate partition with Ubuntu and Grub installed on the Windows partition. The Ubuntu partition(s) would probably not be readable in Windows.

---

### Post by poder39 on 2009-12-04
Thanks a bunch guys! Somehow to timeout or whatever got set to 0, so it didnt give me an option. I reset it to 30 and on bootup it gave me the Ubuntu option again, and it looks like everything is back to normal. Thanks again guys!

---

