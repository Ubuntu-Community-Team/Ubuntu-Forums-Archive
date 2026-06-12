---
title: "Sharing my Ubuntu Live USB Stick with persistent mode"
date: 2011-02-28
forum: General Help
---

### Post by lmarmisa on 2011-02-28
Hi all,

I would like to share my current version of Ubuntu Live USB with some friends who do not use Ubuntu yet. They are Windows users.

I am using a 2 Gbytes USB stick. I created my Ubuntu Live USB with Startup Disk Creator, reserving some extra space for persistence (casper).

I would like to distribute my current Live USB installation to my friends in a simple way.

I don't like to use a solution based on an image of the USB stick made with dd + gizp. This solution would clip to 2 Gbytes the usable memory of a stick in case of recovering it in a stick bigger than 2 Gbytes. Additionally this is inefficient because not only files but also unused areas are stored inside the image of the USB stick.

I have no problem about how to transfer the different files. My problem is how to make bootable the destination USB stick.

I would like to prepare a batch file named makeboot.bat in order to update the MBR of the destination USB stick with a loader for my Live USB. Maybe I need to use some tool like [Syslinux]("http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project"), but I am not sure.

I would appreciate any help for my problem.

Thanks in advance.

Best regards,

Luis

---

