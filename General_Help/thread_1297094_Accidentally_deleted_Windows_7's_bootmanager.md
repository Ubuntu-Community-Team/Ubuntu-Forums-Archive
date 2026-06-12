---
title: "Accidentally deleted Windows 7's bootmanager"
date: 2009-10-21
forum: General Help
---

### Post by gjoellee on 2009-10-21
While running Ubuntu (dual booting) I accidentally deleted Windows 7's boot manager from my harddisk. Now I can't boot to Windows of course. 

I would like to somehow restore Windows 7's bootmanager, but I cannot boot into Windows. I can however access the Windows partition if that helps anything...

Thanks in advance

---

### Post by NightwishFan on 2009-10-21
You can repair grub or the Windows boot using the Super Grub Disk. Or boot into Windows using it. I am not entirely sure if it is compatible to fix the boot of Windows 7. I would try to boot into Windows using it and find a fix from there.

Here is a direct link. You will have to burn it to a CD.
[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso)

---

### Post by PatrickBoyle on 2009-10-21
Boot from the Windows 7 install disc. When it begins the install process it will recognize that there is a Windows partition and give you the option to run a repair. This will fix the MBR and Windows boot menu.

I'm not sure whether your Ubuntu partition will still be an option at boot, but if not you can boot to windows add it from there.

---

