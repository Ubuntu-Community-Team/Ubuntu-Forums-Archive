---
title: "How to change(repair) 0 second boot of windows 7 in ubuntu?"
date: 2011-09-26
forum: General Help
---

### Post by ganesh2shiv on 2011-09-26
Hi there! ):P
I am newbie here at ubuntuforums,
I'm dual booting ubuntu and windows 7.
Actually I'd installed ubuntu in windows 7, so my main/default OS is windows 7.
In hope for making Ubuntu as my default OS, I made a minor tweak in boot options today.
I made changes in 'Startup and Recovery Settings'(System Properties) in windows 7.
But what silly thing I did was changing the time to 0 sec, as I thought  It hardly matters, I'd press arrow keys while booting and the  timer will stop, but It didn't happen so.
So technically I have lost my connection with windows 7, almost.

Can anyone here guide me for changing that 0 sec boot option through Ubuntu or BIOS?
I mean there must be some terminal commands for it.

Curiously waiting for your reply,
Regards,
Ganesh  :popcorn:


Oh btw here are my some system specifications :
Laptop Model :  Sony VAIO VPCEA33EN
OS                 :  Windows 7 Ultimate, Ubuntu 11.04 Natty.

Plz check out this link first, it'll help you in understanding my problem :
"www.lytebyte.com/2009/02/05/how-to-change-the-default-os-boot-order-between-windows-7-and-vista/"

---

### Post by oldfred on 2011-09-26
Is this a wubi install inside the Windows NTFS partition?

If so you have two settings, the first is Windows and the second is grub.

But if it is Windows 7 it is in the BCD and can only be edited from Windows as far as I know. Have you tried f8 as you boot to see if you can get into the Windows recovery mode? You need to use bcdEdit to re-edit the startup time.

If you have a repair CD it can be used. If not make one as soon as you can or make one from a friend who has the same version of Windows 7.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by bcbc on 2011-09-26
The F8 doesn't work according to the many people before you who have done this. I've seen a report that hitting the UpArrow key repeatedly shows the boot manager screen. Try this first.

There's no way to do this from Ubuntu.

The only fix is to boot a Windows repair CD/DVD and modify the timeout: bcdedit /timeout 10  (something like that - refer to Microsoft sites for info, or use bcdedit /? for help). But I've also seen some reports that this doesn't work either - some people have had to rebuild the BCD.

Please let us know what works.

---

