---
title: "disable grub, keep windows boot loader"
date: 2011-12-03
forum: General Help
---

### Post by paradive on 2011-12-03
ok, so i recently had a guy do a reinstall of win7/ubuntu.

he's done this before, but last time there was just the windows boot loader. clean and simple. i want that back.

NOW he has grub going to, so if i select windows from it, it goes to the windows boot loader.
annoyingly redundant...

now, i don't wanna just hide the menu. i wanna get rid of it.
preferably WITHOUT screwing up the MBR so it won't boot anything. :o

thoughts?

---

### Post by dandnsmith on 2011-12-03
What you're talking about is eliminating the GRUB, bootloader and all.
Best way to tackle this is with some sort of Windows repair from install CD - if you don't have one, then possibly google can provide a solution (I don't know the Win7 scene very well yet, having only just started).
You need to repair the boot, and I don't even know what the key terms are for doing it with Win7

---

### Post by oldfred on 2011-12-03
Do you have wubi or a full install?

Without grub you will not be able to boot Ubuntu, but booting Windows should directly boot Windows unless your Windows is configured to boot multiple systems either wubi or XP or something.

Post this from Ubuntu or liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

Or download and install this which gives a gui for simple boot loader fixes & will also run boot info script.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Before you do anything from Windows make a repairCD or USB.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

