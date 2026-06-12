---
title: "Deleting ubuntu partition"
date: 2011-10-13
forum: General Help
---

### Post by headbuster on 2011-10-13
Hello
I would like to know what will happen when I delete the two partition ubuntu created when I installed it: (the 2 on the most right)
[http://i.imgur.com/YOD0b.png]("http://i.imgur.com/YOD0b.png")

I shrunk my DATA partition and then I installed ubuntu.
My question is what will happen to grub when I delete those partitions.

---
Sorry if my q is retarded but I don't know much about boot loaders. Thank you

---

### Post by OpEn_SoUrCe_RoCkS on 2011-10-13
Is this because you want to completely remove Ubuntu from your computer? 
If so, you'll need a tool like [RescaTux]("http://www.supergrubdisk.org/rescatux/").

After burning the tool, try it out. Choose to restore the Windows MBR.

Now, make sure Windows boots (without Grub).

You may now delete the Ubuntu partitions from Windows.

---

### Post by headbuster on 2011-10-13
Is this the only way? Also what will happen if I delete the partition without doing this?

---

### Post by oldfred on 2011-10-13
Computer boot thru the MBR. The MBR is tiny and refers to additional code on the hard drive. If you delete the Ubuntu partition the grub2 boot loader will not find any files and just crash with a grub>.

You need to isntall the Windows boot loader. 

Another way.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Do you have the Windows repair CD? You should have a repairCD for every system installed just in case.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by headbuster on 2011-10-13
I burnt a new windows recovery disk, went to cmd and did bootrec/fixboot, bootrec/fixmbr.
Now I will delete the ubuntu partition.
Thank you

---

