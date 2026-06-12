---
title: "The Uninstallation Process"
date: 2011-09-26
forum: General Help
---

### Post by fl00ky on 2011-09-26
Note: While I do want to uninstall Ubuntu, this thread is for information regarding the installation process. I.E to better understand how it's accomplished. I do plan on putting it back. 

**Current Setup : **Single laptop. 2 physical HDD. Windows 7 on drive 1. Ubuntu 10.4 on Drive 2.

**What I Know : **I know I can use Windows' in-built disk management utility to format the second HDD and partitions. 

My computer currently boots to the 'Grub OS choice page. Having been through a couple of threads, I have an idea of what the uninstallation process entails when using a single HDD. 

So, I just format the second HDD through Windows 7 and then fix the boot loader. 

**What I want to know : **

1) How does the process work when each OS is on a separate physical HDD?

2) I assume I'd have to fix the boot loader regardless. If so, is it possible to run the fix without the Windows DVD? I relocated to the States from Canada and by mistake left all my recovery disks, etc. back there. As such, is there a way to access the recovery console without using the DVD?

As always, thanks for your time and I appreciate any help I can get.

---

### Post by oldfred on 2011-09-26
If you have two drives, you have two MBRs and one can be grub2's boot loader and the other Windows boot loader. That way each drive has its own system and boot. Have you in BIOS tried booting the other drive? Or is grub2's boot loader in the Windows drive. Often default install of grub is to the MBR of sda.

To see what is where.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

You should have a Windows repairCD.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by fl00ky on 2011-09-28
Hey,

Thanks a lot for the links. I've not been through all of them as I've been very busy. I'm going to try and make some time over the weekend and I'll get back to you. 

I appreciate it.

Thanks.

---

