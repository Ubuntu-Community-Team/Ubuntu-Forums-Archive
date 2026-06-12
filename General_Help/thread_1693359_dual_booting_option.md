---
title: "dual booting option"
date: 2011-02-22
forum: General Help
---

### Post by Arushan on 2011-02-22
hi once i install ubuntu on a separate hard drive in my computer how do i get it to show if i want to boot xp or ubuntu? 

*xp on seperate hdd
*ubuntu on seperate hdd
so 2 hdd in total

---

### Post by JRV on 2011-02-22
The grub2 boot loader should find XP and give you the option to boot either automatically.

---

### Post by drs305 on 2011-02-22
As JRV stated, Grub2 will find the Windows OS and include it on the Grub2 menu.

One thing you can do during the installation is to install G2 only to the second drive's MBR. After the installation is complete, as the computer reboots enter the BIOS and change the boot order so the Ubuntu drive boots first. You will then get the G2 menu.

The advantage of doing this is that Grub2 will control the Ubuntu MBR and Windows will still control the MBR of the Windows drive (although it won't be used). If you ever have a problem with the Grub menu and need to get back to Windows quickly, you can switch the BIOS to boot the Windows drive first, and you will be greeted with the Windows menu when you reboot.

---

### Post by samacaster on 2011-02-22
Your second drive is set secondary (Primary Slave) I'm assuming (this can be checked in your BIOS) If it is just stick the CD in the drive and make certain you choose the correct drive for installation.
When you come to the part of the installation that asks where to install the bootloader (Grub2) you'll have a decision to make. Which drive to put the bootloader (Grub2) on?

To be safe, and for the sake of not losing your MBR, I would install the bootloader onto the same drive as your Ubuntu installation. Just before the installation finishes, Grub will update. It will scour the drives to find any bootloaders, MBR's, etc... and automatically add them to the boot options.

When you reboot after installation, you'll see the grub menu.

---

### Post by Arushan on 2011-02-23
ok thanks for the much need info

---

