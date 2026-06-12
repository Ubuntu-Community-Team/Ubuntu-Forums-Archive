---
title: "Start up menu"
date: 2012-05-11
forum: General Help
---

### Post by jpaulb on 2012-05-11
I have been trying different Ubuntu distro on a Window 7 box. I remove the distro the and later boot into windoze I still have the option of booting the removed distros. At the present time my options are Windows 7, Ubuntu, Lubuntu even when Win 7 is the only installed OS
 If I try booting one of the non Windows OS GRUB naturally warns me it does not exist

How do I remove these entries from the window 7 Boot menu?

Thanks

Paul

---

### Post by westie457 on 2012-05-11
Take a look here for your options.

[http://blog.eukhost.com/webhosting/howto-remove-grub-loader-and-restore-windows-7-and-vista-bootloader/](http://blog.eukhost.com/webhosting/howto-remove-grub-loader-and-restore-windows-7-and-vista-bootloader/)

---

### Post by wilee-nilee on 2012-05-11
> **jpaulb said:**
> I have been trying different Ubuntu distro on a Window 7 box. I remove the distro the and later boot into windoze I still have the option of booting the removed distros. At the present time my options are Windows 7, Ubuntu, Lubuntu even when Win 7 is the only installed OS
 If I try booting one of the non Windows OS GRUB naturally warns me it does not exist

How do I remove these entries from the window 7 Boot menu?



Thanks

Paul

Whatever distro is at the top of the grub menu is the grub control, run a update grub in it, if it is wubi don't run the update. If you are using easybcd tell us, open it and remove the notations.

Your thread says wubi but you can only have one install of it I believe this a confusing thread honestly.

---

### Post by jadtech on 2012-05-11
if it is wubi it leaves a line in windows boot.ini file just comment out the ubuntu  line and you should be good to go ..

---

### Post by bcbc on 2012-05-12
Refer to the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F"):
> To use bcdedit, run cmd.exe as an administrator, then enter bcdedit to show all boot entries, note the {GUID} specified for the Ubuntu entry, and then remove it: bcdedit /delete {GUID}

e.g.
```
C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume2
description             Windows Boot Manager
locale                  en-us
inherit                 {globalsettings}
default                 {current}
resumeobject            {6529eb15-62be-11e0-b237-a8486d1f5063}
displayorder            {current}
                        {c001df0c-5ec0-11e1-a466-005056c00008}
toolsdisplayorder       {memdiag}
timeout                 10

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-us
inherit                 {bootloadersettings}
recoverysequence        {6529eb17-62be-11e0-b237-a8486d1f5063}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {6529eb15-62be-11e0-b237-a8486d1f5063}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {c001df0c-5ec0-11e1-a466-005056c00008}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

C:\Windows\system32>bcdedit /delete {c001df0c-5ec0-11e1-a466-005056c00008}
```

---

### Post by jpaulb on 2012-12-09
> **jadtech said:**
> if it is wubi it leaves a line in windows boot.ini file just comment out the ubuntu  line and you should be good to go ..

Has it been that long since I used windoze?
Where do I find this boot.ini file?

In Nautilus I have under devices, OSDisk, which is the Windows 7 distro. There is not file at / called boot.ini, or in the boot folder. That that contains a dozen or so language folders, fonts folder, BCD, BCD.log, BOOTSTRAP.DAT and memtest.exe
```
/media/OSDisk$ find -name boot.ini 
``` returns nothing

---

### Post by jpaulb on 2012-12-09
[QUOTE=bcbc;11927905]Refer to the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F"):

To use bcdedit, run cmd.exe as an administrator, then enter bcdedit to  show all boot entries, note the {GUID} specified for the Ubuntu entry,  and then remove it: bcdedit /delete {GUID}
-------------------

Thanks the Windows boot loader now works.=D>
I have been away from Windows since XP was in Beta stage

---

