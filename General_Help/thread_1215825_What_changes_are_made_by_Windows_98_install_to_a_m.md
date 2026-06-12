---
title: "What changes are made by Windows 98 install to a multi boot?"
date: 2009-07-17
forum: General Help
---

### Post by hissyfut on 2009-07-17
Attempting to add windows 98 to a multi boot system for a friend's computer. The system has xp and ubuntu, and now is to install windows 98 on the extended partition in a fat logical partition. Grub is on the logical of extended boot partition of ubuntu, and boot options for system are handled by a separate boot loader.

What will windows 98 change after it is installed?
Will it erase the MBR?
Will it set it's install partition as the boot partition?

To answer some possible "why" questions:
Do not want to alter boo.ini of xp since a separate boot loader is used, and do not want to use the boot.ini of xp to boot to 98.

To sum up, needing to install 98 on it's own logical partition and fixing what it changes.

---

### Post by Herman on 2009-07-17
That's quite an unusual thing to do, adding Windows 98 when you already have Windows XP. 
Windows XP is supposed to do everything Windows 98 can do, plus much more. 
Most people would start with Windows 98, and if their computer is capable of it, add Windows XP after Windows 98. What you want to do is backwards.
If there's something Windows XP can't run that you need Windows 98 for, you should try using something called 'backwards compatability mode', (or something like that, I can't remember exactly), which allows Windows XP to run programs designed for earlier Windows systems.
There should be no need for Windows 98 if you already have XP.

---

### Post by aysiu on 2009-07-17
> **Herman said:**
> That's quite an unusual thing to do, adding Windows 98 when you already have Windows XP. 
Windows XP is supposed to do everything Windows 98 can do, plus much more. 
Most people would start with Windows 98, and if their computer is capable of it, add Windows XP after Windows 98. What you want to do is backwards.
If there's something Windows XP can't run that you need Windows 98 for, you should try using something called 'backwards compatability mode', (or something like that, I can't remember exactly), which allows Windows XP to run programs designed for earlier Windows systems.
There should be no need for Windows 98 if you already have XP.
Don't forget that Windows 98 no longer receives security updates from Microsoft.

---

### Post by Herman on 2009-07-17
Windows has a very peculiar way of setting up a dual boot if you allow it to do as it pleases. 
If you already have Windows 98 and you want to add Windows XP, and you allow Windows to do as it pleases, it will set up a 'microsoft default dual boot'.
Your new Windows installation, (normally XP), will add it's boot loader and boot loader files to Windows 98, which is normally in the primary partition. Then Windows XP installs itself automatically in a logical partition with no boot loader of it's own. 
The problem is, if the user later deletes the older operating system, they also delete the boot loader for their newer Windows installation, leaving the more modern Windows unbootable until it is repaired.

If you use GRUB, you can set up your Windows-Windows dual boot without that problem.
GRUB's 'hide' and 'unhide' commands may be used to set the 'hidden flag' in the partition table on the existing Windows in the primary partition, that way the new install doesn't 'see' the existing Windows, and it will install in another primary partition, keeping its boot loader files for itself.
Later, you can edit the GRUB menu to 'hide' the Windows you don't want to and 'unhide' the Windows you do want to boot and set the boot flag on it t boot-up.
The 'hidden' flag doesn't work for Windows Vista or Windows 7 because those are now programmed to ignore the 'hidden' flag, and can even detect an earlier Windows in a different hard disk.

The goal for most people is to get the newer Windows to install in a primary partition since it's not so simple to get Windows to boot by itself in a logical partition.
I have managed to do it by using a partition editor to place the boot flag in the logical partition, GRUB can't do it.
Your goal of installing Windows in a logical partition is another thing you're doing that's backwards, and the opposite of what most people would want to do if you want to be able to boot your Windows without too much difficulty. 

If you succeed in getting Windows 98 installed in a logical partition while another Windows is in a primary, you can expect booting to be complicated if not impossible.

Actually, I doubt if you'll even be able to get the installation started, because in my experience, Windows 98 will refuse to install if it detects any logical partition in the hard disk. I have always had to delete my Ubuntu swap area to re-install Windows 98, because it was normally in a primary partition. At least the Windows 98 CD I have won't install if a logical partition exists in the hard disk. Yours might be different than mine. I do know that not all Windows installation CDs are the same, but vary according to the different computer manufacturers they were sold to.

---

### Post by Herman on 2009-07-17
> Don't forget that Windows 98 no longer receives security updates from Microsoft. :) Yes, that's right too, aysiu.

hissyfut,
If you're having fun, I don't mean to be a wet blanket, go ahead with your experiment and and try it and see what happens and have fun. But, be aware that what you're about to do might be unnecessarily complicated and unnecessary.

I do things myself that are unnecessarily complicated and unnecessary, in fact, I go right out of my way sometimes to do so, all in the name of fun, and to satisfy my curiosity.
If it's just for fun though, you should probably be using your own computer for that instead of a friend's computer, unless you're both having fun together.

You might want to record the results of your experiment, and what problems you run into, and how you solve them. That's what I try to do, so I can help others later.
Experimenting with installing operating systems and playing with boot loaders is a good way to learn about computers. 

Regards, Herman :)

---

### Post by konnorrigby on 2009-07-17
Why would you install windows 98? if you really want to, get Qemu for your windows XP partition and just make an iso of the install disk and use it from there its funner this way.    :)

---

### Post by Herman on 2009-07-17
:idea: I just thought of a good idea. (Well, at least I think it is).

Windows 98 uses hardly any RAM, so it's an ideal candidate for installing inside Ubuntu. You can install Windows 98 inside Ubuntu using virtual box or vmware player. Then you can have both operating systems running at once! It's a great trick because you can have Windows in one workspace and switch to Ubuntu whenever you like. That's useful for some people who want to be able to use Ubuntu but can't do without some program that will only run in Windows.
Running two operating systems at once takes a lot of RAM and slows the computer down, but Windows 98 probably won't slow the computer down as much as Windows XP, so it would be ideal for that purpose.
There are how-tos in this web forum's [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100") about vmware player or virtual box and other emulators.

EDIT: Or Qemu, I agree with konnorrigby, sorry, I didn't see the above post before clicking to add mine.

---

