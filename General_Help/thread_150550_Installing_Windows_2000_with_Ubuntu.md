---
title: "Installing Windows 2000 with Ubuntu"
date: 2006-03-26
forum: General Help
---

### Post by elm0 on 2006-03-26
I am trying to install Windows 2000 to make it dual-boot with Ubuntu. I did not have a DOS bootdisk or a burner on this computer, so I formatted the harddrive with the Ubuntu setup disc. The disc won't let me just format though, after that it continues to install, so now I have just Ubuntu on my computer, and I would like to put Windows 2000 on it for gaming. Here's the thing though. I have no DOS bootdisk to do fdisk /mbr, and I installed GRUB to the MBR. My Windows 2000 CD won't boot up before the computer starts (maybe thats because it was burnt?). It has BOOTDISK folder on it though, it was burned at work for me. The computer recognizes it's there because it stays at "Boot from CD..." for a while, just never does. So...shouldn't my Win2k disc boot anyway? Perhaps I can burn the 4 Win2k discs on bootdisk.com and fix this problem? Or is there a way to format the MBR in Unix? I've been looking for help all over Google and didn't find it, so I finally posted here.

---

### Post by el3ktro on 2006-03-26
[QUOTE=elm0]I am trying to install Windows 2000 to make it dual-boot with Ubuntu. I did not have a DOS bootdisk or a burner on this computer, so I formatted the harddrive with the Ubuntu setup disc. The disc won't let me just format though, after that it continues to install, so now I have just Ubuntu on my computer, and I would like to put Windows 2000 on it for gaming. Here's the thing though. I have no DOS bootdisk to do fdisk /mbr, and I installed GRUB to the MBR. My Windows 2000 CD won't boot up before the computer starts (maybe thats because it was burnt?). It has BOOTDISK folder on it though, it was burned at work for me. The computer recognizes it's there because it stays at "Boot from CD..." for a while, just never does. So...shouldn't my Win2k disc boot anyway? Perhaps I can burn the 4 Win2k discs on bootdisk.com and fix this problem? Or is there a way to format the MBR in Unix? I've been looking for help all over Google and didn't find it, so I finally posted here.[/QUOTE]

Honestly, you better get a legal copy of Win 2000, then it will also boot fine. You should install Win 2000 first (creating only a small partition for Windows, leaving the rest of your harddisk empty). AFTER you've installed Windows, you can install Ubuntu. Ubuntu will detect that Windows is installed and setup dual booting for you.

Tom

---

### Post by halitech on 2006-03-26
if it has the bootdisk folder, there should be 4 or 5 files in there, you would need something like rawwrite to put the disk images on the floppies then you can use that to boot. Also, if it is saying "Boot from CD..." if you hit Enter or the Spacebar, it will start the actual boot process from the cd (or at least it does with mine). If you install Windows first, you will need to redo GRUB though as Windows likes to be the only game in town.

---

