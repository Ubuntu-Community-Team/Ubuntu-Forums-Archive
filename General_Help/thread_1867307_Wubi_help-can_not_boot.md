---
title: "Wubi help-can not boot"
date: 2011-10-22
forum: General Help
---

### Post by giobasi on 2011-10-22
I have installed wubi ubuntu 11.10 with windwos 7 

when boot normal I see black screen with cursor, than I use ubuntu  LiveCD to boot fom hard disk. 

I read this [http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

and did this:

     Code:
     gksudo gedit /etc/default/grub 
a text editor will open with the grub configuration file. Near the top of that file you will see something very similar to this:
     Code:
     GRUB_DEFAULT=0 #GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=10 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** GRUB_CMDLINE_LINUX="" 
add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line, so for instance:

     Code:
     GRUB_DEFAULT=0 #GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=10 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"** GRUB_CMDLINE_LINUX="" 
Save the file and exit gedit. If you have to add kernel options that contain quotation marks, add them as such:

     Code:
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=[COLOR=Red]\"[/COLOR]Linux[COLOR=Red]\"[/COLOR]" 
Now in the terminal, run the following command to update your grub configuration with the new default settings:
     Code:
     sudo update-grub 


but problem not SOLVED!!!! I see black screen with cursor and I can boot only with LiveCD-boot from first hard disk

plz help :(

---

### Post by utnubuuser on 2011-10-22
You might change your topic title to something like WUBI help - can't boot, so viewers can see what you need help with..

---

### Post by giobasi on 2011-10-23
> **utnubuuser said:**
> You might change your topic title to something like WUBI help - can't boot, so viewers can see what you need help with..

ok thx

up
u&#4323;p
:confused:

---

### Post by giobasi on 2011-10-23
&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;&#4323;

---

### Post by cozumel on 2011-10-23
Hi,

Firstly I know nothing about wubi but just wanted to check if you had attempted an install on to RAID array or encrypted disk.

Also have you tried from Windows chkdsk /r on the disk that contains ubuntu?

---

### Post by oldfred on 2011-10-23
Edited top level title for you.

Do you have a liveCD, It is often a good idea. But if booting with Windows you definitely need a Windows repairCD.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You can download a repairCD and from that post a link to boot_info script results which will show your configuration. If a video issue that may not help but if a boot issue it will.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by giobasi on 2011-10-24
> **oldfred said:**
> Edited top level title for you.

thx

> **oldfred said:**
> Do you have a liveCD, It is often a good idea. But if booting with Windows you definitely need a Windows repairCD.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You can download a repairCD and from that post a link to boot_info script results which will show your configuration. If a video issue that may not help but if a boot issue it will.

thx but I have not problem with windows,  boot normally

> **oldfred said:**
> Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

ok I'll try it ;)

---

### Post by giobasi on 2011-10-24
> **cozumel said:**
> Hi,

Firstly I know nothing about wubi but just wanted to check if you had attempted an install on to RAID array or encrypted disk.

Also have you tried from Windows chkdsk /r on the disk that contains ubuntu?

I try install normally with CD but same boot problem. Nothing more

---

### Post by giobasi on 2011-10-24
[http://paste.ubuntu.com/718150/](http://paste.ubuntu.com/718150/)

---

### Post by oldfred on 2011-10-24
I do not know much about wubi.

It looks like you installed wubi to the hidden 100MB boot/recovery partition for Windows sda1 and now it does not show the boot files. That partition is normally too small for a wubi install.
Script also now shows Windows boot flag on sda2 which looks like your main (c:) partition.

It looks like you now need that windows repair CD.

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by giobasi on 2011-10-24
> **oldfred said:**
> I do not know much about wubi.

It looks like you installed wubi to the hidden 100MB boot/recovery partition for Windows sda1 and now it does not show the boot files. That partition is normally too small for a wubi install.


thxxxx, yesss solved, I delete this 100 mb partition, and than uninstall /install new wubi 11.10,after instal  there was not boot entry for ubuntu in windwos loader and I add from command prompt:


bcdedit /create /d ubuntu /application BOOTSECTOR

You’ll need to replace {ID} by the actual returned identifier. An example of {ID} is {d7294d4e-9837-11de-99ac-f3f3a79e3e93}.

bcdedit /set {ID} device partition=E:

The path to ubuntu\winboot\wubildr.mbr file:

bcdedit /set {ID}  path \ubuntu\winboot\wubildr.mbr

An entry to the displayed menu at boot time:

bcdedit /displayorder {ID} /addlast

:D

---

### Post by oldtimer7777 on 2011-10-24
I've seen many problems with Wubi. It is really only to be used to try Ubuntu out briefly for a while.. It isn't for long term usage.  I suggest creating a USB Live Stick of Ubuntu instead, and try using Ubuntu that way for a while.  If you want it, then you can install it:
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **giobasi said:**
> thxxxx, yesss solved, I delete this 100 mb partition, and than uninstall /install new wubi 11.10,after instal  there was not boot entry for ubuntu in windwos loader and I add from command prompt:


bcdedit /create /d ubuntu /application BOOTSECTOR

You’ll need to replace {ID} by the actual returned identifier. An example of {ID} is {d7294d4e-9837-11de-99ac-f3f3a79e3e93}.

bcdedit /set {ID} device partition=E:

The path to ubuntu\winboot\wubildr.mbr file:

bcdedit /set {ID}  path \ubuntu\winboot\wubildr.mbr

An entry to the displayed menu at boot time:

bcdedit /displayorder {ID} /addlast

:D

---

### Post by giobasi on 2011-10-24
> **oldtimer7777 said:**
> I've seen many problems with Wubi. It is really only to be used to try Ubuntu out briefly for a while.. It isn't for long term usage.  I suggest creating a USB Live Stick of Ubuntu instead, and try using Ubuntu that way for a while.  If you want it, then you can install it:
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

ok, ;)

---

