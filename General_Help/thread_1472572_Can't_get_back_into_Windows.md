---
title: "Can't get back into Windows"
date: 2010-05-04
forum: General Help
---

### Post by paulw280 on 2010-05-04
Hi folks,

As a new user of Ubuntu, I seem to have gotten a bit overzealous and gotten myself into a problem.  I've managed to install Ubuntu 9.10 on a Compaq CQ50 Laptop so that it dual-boots with Windows Vista.  Everything initially was working fine - Vista and Ubuntu worked side by side pretty well, and it all seemed hunky dory, until I shot myself in the foot.
Basically, whenever the computer was booting I would first see the Windows Boot Manager, followed by the GRUB boot manager when Ubuntu was selected.  Since both boot loaders had options to boot into the other OS, I figured that it wouldn't hurt to set Windows Boot Manager to 0 seconds display time, thus removing one small step in the booting process.
Unfortunately, now when I choose to boot into Windows via GRUB, it briefly flashes up with the Windows Boot Manager and then kicks back to GRUB, and nothing I do seems to let me get back into Windows.
I've tried booting from a Vista disk and using Bootrec /FixBoot, I've tried reinstalling GRUB and getting it to update its boot tables, I even tried installing LILO.  So far, nothing seems to be working.
If anyone could give me any pointers on this, I'd very much appreciate it!

---

### Post by mk1w86 on 2010-05-04
When you installed Ubuntu did you let it automatically configure dual boot or did you set something up yourself?  You do not normally boot grub/Ubuntu from the Windows boot loader. :confused:

---

### Post by paulw280 on 2010-05-04
To be honest, I really don't know what was done.  The entire installation process was a royal headache from the get-go - first none of the images I burned to disk would install from boot (they'd either crash or slow down the computer to the point of unusability), then WUBI wouldn't reboot the computer automatically... in the end I managed to get WUBI to install from inside Windows by copying the ISO file to the same folder (which seemed odd since I was running WUBI initially from the image burned from the ISO that I had to put into the same directory?!?!?)
Anyway, all I know was that when it was all running ok, the first boot screen would be the Windows one offering the choice of Vista or Ubuntu.  If Ubuntu was selected, it'd then go to GRUB where the choices were Ubuntu, Ubuntu recovery, or two Windows partitions - the first being the actual Vista partition, and the second a recovery drive.

---

### Post by dino99 on 2010-05-04
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

into ubuntu, open a console, then: sudo grub-mkconfig && update-grub

sudo update-initramfs -u

---

### Post by mk1w86 on 2010-05-04
Ahh, so you installed using Wubi, I thought you had set up a proper dual boot.  That explains why you are using the Windows bootloader. #-o

I know a lot of people have had problems with Wubi in Ubuntu 9.10 (I don't know if it's any better in 10.04).  I would recommend you install Ubuntu to its own partition but first we obviously need to get Windows booting.

It is probably worth trying the automatic Startup Repair on your Vista install disk first and see if that allows you to boot Windows.  Otherwise you might have to try the Bootrec /FixMbr or one of the other options to try and remove the Ubuntu boot entry, there is more information here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by dino99 on 2010-05-04
sorry i've not seen that WUBI thing, better to use virtualbox

---

### Post by mk1w86 on 2010-05-04
> **dino99 said:**
> sorry i've not seen that WUBI thing, better to use virtualbox

Wubi is not a virtual machine, there is more information on it here:

[http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer](http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer))

---

### Post by dino99 on 2010-05-04
> **mk1w86 said:**
> Wubi is not a virtual machine, there is more information on it here:

[http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer](http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer))

i'm not so crazy to install ubuntu into a windoz file  :lolflag:

---

### Post by paulw280 on 2010-05-04
I have a 120GB internal hard drive, partitioned thusly:

SDA1 - 59GB NTFS, Vista Installation
SDA2 - 40GB NTFS, Files/data storage
SDA3 - 12GB Extended Partition on which is SDA5 - NTFS, Ubuntu installation
SDA4 - 9.4GB NTFS, Recovery partition

Until now I didn't realise that the Ubuntu installation was on an extended partition, or using the NTFS file system.  Could this be where the problem is?

---

### Post by paulw280 on 2010-05-04
Thanks for the pointers guys.  I'm going to try using the Bootrec /FixMBR and see how that goes.  If it works, I'll re-jig my partition arrangement and make a decent bootable disk for Ubuntu.

---

### Post by paulw280 on 2010-05-04
Or not.  Even fixmbr didn't work!  The only thing I can assume is that there is nothing wrong with the MBR and bootloaders themselves - the problem seems to be that because I set the time for Windows Boot Loader to display options to 0 seconds, and because when GRUB tries to boot Windows it goes back to the Windows bootloader, then it ends up being a never ending loop.  Only thing I can think of is to uninstall Ubuntu, :(

---

### Post by mk1w86 on 2010-05-04
After some Googleing (and struggling to get my Windows 7 disk to boot in Virtual Box to try it :-x) I found out about the BCDEdit command.  You should be able to run it from your Vista disk and use it to change the countdown timer or the default boot entry of the Windows Boot Manager. :D

[http://technet.microsoft.com/en-us/library/cc709667(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc709667(WS.10).aspx)

---

