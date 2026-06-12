---
title: "Can't boot back into Windows"
date: 2012-08-01
forum: General Help
---

### Post by Chris the Noob on 2012-08-01
I apologize if I've posted this is the wrong place, but I wasn't sure where else to post it. After installing Ubuntu with Wubi, I set Ubuntu as the default OS in Windows and set the Windows boot menu to appear for 0 seconds in order to keep things as streamlined as possible. However, I now can't figure out how to boot back into Windows. I have tried pressing F8 and arrow keys as my computer boots up to no avail. I have no Windows repair disc, either.

If it makes any difference, I'm using a Lenovo B570.

---

### Post by G4dget on 2012-08-01
I am unfamiliar with wubi so I may don't be able to help very much at all but maybe get some good brainstorming going. 

1. Is there any kind of boot screen at all or does it always boot directly into ubuntu without any pause at all?

2. Is there a reason not to use Grub to handle booting the OS (again unfamiliar with wubi) but I have always had good luck with using Grub to handle these things. This can be installed and updated through ubuntu.

3. What version of windows are you using?

4. Do a search based on your windows version about what key and when to interrupt the boot loader (xp I remember is F8 , at least I thought)

---

### Post by Chris the Noob on 2012-08-01
Thanks for the reply, G4dget.

1. There is a screen that appears briefly before booting into Ubuntu. All it has is the Lenovo logo and the options to press F2 for setup (I didn't find this helpful in my case) or F12 to go to a boot menu, which allows me to boot from the hard drive, a CD, etc. However, no matter what I do, the Windows boot screen is always skipped, taking me right to Ubuntu.

2. I don't think Wubi uses Grub by default (it may not be compatible), but I'll try it. 

3. I am using Windows 7, it came pre-installed.

4. To tell you the truth, I'm not entirely sure that F8 is the correct key for Windows 7. I'll look into it.

---

### Post by oldfred on 2012-08-02
See post #4, by bcbc who really knows wubi.

[http://ubuntuforums.org/showthread.php?t=2035621&highlight=bcdedit](http://ubuntuforums.org/showthread.php?t=2035621&highlight=bcdedit)
> I believe the only way to fix it is to boot from a Windows 7 repair CD and change the timeout:
bcdedit /timeout 10

If you know someone with Windows 7 and the same 32 or 64 bit version:

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


We used to have a free site to download the repair only CD but now they want $10.

---

### Post by G4dget on 2012-08-02
If you just need to edit the boot file to prolong the OS boot screen this could be done jin ubuntu. I know for xp the file is boot.ini in the root of the boot drive (not sure about 7). Just open it with you editor of choice and edit the line suggested.

---

