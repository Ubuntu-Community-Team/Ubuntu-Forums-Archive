---
title: "Installing on seperate hard drives"
date: 2011-10-22
forum: General Help
---

### Post by jaj44uk on 2011-10-22
Hey everybody.

I'm hoping somebody can help me.

I have windows 7 on my RAID 0 (2x1TB array) and i found an old 60GB hard drive lying around and thought that I'd like to put ubuntu on it to do all of my android coding. The problem is I want to be able to boot of the drive without upsetting any of the boot menus on my windows 7 array.

I thought that if i installed 11.10 from the live cd and just selected my 60Gb drive as the device to install the bootloader on that i would just be able to select that drive from my BIOS boot menu and it would boot no problem.

Unfortunately that is not the case and my computer just boots to windows when selecting my 60GB from the bios. Has anyone any idea where i am going wrong. I have read other threads and guides online but havnt made any progress.

Thanks in advance
James

---

### Post by cozumel on 2011-10-22
See [this thread]("http://ubuntuforums.org/showthread.php?t=1640178"), in particular post #4


> Disconnect your Windows drive and install Ubuntu on the second drive. Make sure Ubuntu works the way you want it then power down and re-connect the Windows drive. Reboot the computer and Ubuntu should restart with a boot screen giving you the option of starting Ubuntu (default) or Windows. At this point, you have made no changes to the Windows drive. You can then use the boot manager in Ubuntu to select which OS is default. Alternatively, reset the boot drive order in the BIOS so that Windows boots first and select the Ubuntu drive during the boot process when desired. I use Gigabyte motherboards and hitting the F12 key a few times during the boot process will bring up the menu allowing selection of the boot device. This is the way I do it and it has the advantage of leaving the boot sector on the Windows drive completely intact so that you could remove the drive containing Ubuntu and still be able to boot Windows.

---

### Post by WorMzy on 2011-10-22
I recommend that you boot to a liveCD and run the following script: [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/"), then post the outputted document here.

---

### Post by jaj44uk on 2011-10-23
Hey guys thanks for the help. I tried installing while the windows array was unplugged and it works and boots fine. Plugged my windows drive back in and when I use the bios boot menu to choose my ubuntu disk it just boots windows.

Been playing around though and I think its my bios that's being a bit dodgy. If the windows drive is first in boot priority and I choose the linux drive I go to windows. But if I change the boot order for linux first it does actually boot to grub. With the boot menu choice actually having no effect when the linux drive is selected.

I think all that I need to do now is add a windows entry to grub and keep the boot settings the way they are and I'm all set. Thanks for the help.
James

---

