---
title: "Wubi Installed Ubuntu Doesn't Allow choose OS"
date: 2012-03-16
forum: General Help
---

### Post by webmanoffesto on 2012-03-16
I'm running a recent version of Ubuntu as a dualboot (Wubi installed). Now when I reboot my computer I get to the screen (GRUB?) where Windows 7 is the default OS and I can down-arrow to boot into Ubuntu. But the down-arrow (and up arrow and letter keys) don't do anything, so the computer does a default boot into W7. I want to bet back to Ubuntu without reinstalling it. What should I do?    webmanoffesto

---

### Post by YannBuntu on 2012-03-16
Hello

You can use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")'s recommended repair to get access to your Wubi documents (it will open a file browser for this) and backup them. Then it will propose to try a filesystem repair.
Reboot , then check if you can access Wubi. If still not good, i recommend you install Ubuntu the standard way (without Wubi = OUTSIDE Windows = on a separate partition). Wubi is ok to test Ubuntu, but for normal use it's safer to use standard Ubuntu installation.

EDIT: sorry i made mistake, please look at bcbc answer below.

---

### Post by bcbc on 2012-03-16
It sounds like the keyboard is not working as the OP said the down arrow won't allow Ubuntu to be selected - it doesn't mean Wubi is broken.

---

### Post by bcbc on 2012-03-16
> **webmanoffesto said:**
> I'm running a recent version of Ubuntu as a dualboot (Wubi installed). Now when I reboot my computer I get to the screen (GRUB?) where Windows 7 is the default OS and I can down-arrow to boot into Ubuntu. But the down-arrow (and up arrow and letter keys) don't do anything, so the computer does a default boot into W7. I want to bet back to Ubuntu without reinstalling it. What should I do?    webmanoffesto

I assume it used to work - is this true or have you just installed Wubi? When your computer boots, does the keyboard work e.g. to enter BIOS? 
If it was booting ubuntu before, has something changed recently?

---

### Post by webmanoffesto on 2012-03-17
Yes, my dual boot (Wubi) was working fine for a couple of months (including selecting the OS using Grep with down arrow).  Right now, after default booting into W7 my keyboard (and arrows) work fine.

---

### Post by bcbc on 2012-03-17
The screen that offers the choice of Windows and Ubuntu (just those two) is the Windows boot manager (it should say that at the top), not the grub menu. 

So are you saying that the keyboard (arrow keys) no longer work when you are on the windows boot manager? Because once the Windows OS is booted the hardware is accessed through more advanced drivers than what is available at boot time.

It's not unheard of to have a keyboard not work in BIOS, but work once the OS is booted (normally with a USB keyboard). That's why I asked if you can enter BIOS (e.g. F2 or Esc keys - it should say what key you need) and use the keyboard there.

Was there anything that happened just before things stopped working that you can recall? Because it's unusual for this to happen out of the blue.

---

### Post by webmanoffesto on 2012-03-20
When I go to the BIOS the arrow keys do work. When I get to the "Choose W7 or Ubuntu" screen the arrows do not work. 

Yes, there was a brief period when my computer wouldn't boot into anything. Some fiddling resolved it, maybe it was attempting a Windows Recovery, which said it didn't fix the problem but then after reboot it booted into W7 fine.

---

### Post by bcbc on 2012-03-20
Go to an administrator command prompt and run:
```
bcdedit
```

Please post the result.

PS to get to the prompt, click window start button, type 'cmd' but don't press enter. Look above, right click on CMD.EXE and select "Run as administrator".

---

### Post by webmanoffesto on 2012-03-21
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {0e8541fc-258f-11dc-8b1e-82dc7104e7f6}
displayorder            {current}
                        {0e854201-258f-11dc-8b1e-82dc7104e7f6}
toolsdisplayorder       {memdiag}
timeout                 10

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {0e8541fe-258f-11dc-8b1e-82dc7104e7f6}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {0e8541fc-258f-11dc-8b1e-82dc7104e7f6}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {0e854201-258f-11dc-8b1e-82dc7104e7f6}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

C:\Windows\system32>^A

---

### Post by bcbc on 2012-03-21
That looks fine... identical to my own install.

Please review this and see if anything applies: [http://social.technet.microsoft.com/Forums/en-US/w7itproinstall/thread/4913d263-4921-44c3-8b84-cc1526140464](http://social.technet.microsoft.com/Forums/en-US/w7itproinstall/thread/4913d263-4921-44c3-8b84-cc1526140464)

It seems a bit unlikely if it's working in BIOS, and in Windows, but not in the boot manager, however in that post I linked to the same symptoms were found and the problem turned out to be some bios setting.

---

### Post by 3rdalbum on 2012-03-21
I'd say, definitely look in the BIOS settings. There's a setting usually called "Plug 'n' Play OS" that might need to be toggled. Or, there's a setting like "Legacy keyboard emulation". These settings don't really do anything different for the end user or the OS once it's loaded, but turning on legacy keyboard emulation and toggling Plug 'n' Play OS may help the Windows bootloader or GRUB to use the keyboard before any drivers are available.

---

### Post by webmanoffesto on 2012-04-12
1. Uninstalled Wubi Ubuntu. Reinstalled Wubi Ubuntu. Still had same problem.   2. Unplugged USB Keyboard, replaced it with my old PS/2 Keyboard, problem solved. I still have to check if, after booting into Ubuntu, I can unplug my old PS/2 keyboard and use my new USB keyboard.   . Have you seen this problem. Is there a solution other than "keep using the old PS/2 keyboard"?

---

