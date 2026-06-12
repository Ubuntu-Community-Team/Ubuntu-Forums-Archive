---
title: "grub error and failure to boot into vista or ubuntu"
date: 2009-07-01
forum: General Help
---

### Post by atomsmasherr on 2009-07-01
One of my friends thought he knew an easy way to uninstall Ubuntu from my computer but he only complicated the problem. He told me to go to "Control Panel > Administrative Tools > Computer Management > Disk Management" and delete one of the partitions. Once I did that all was normal until i rebooted my computer this morning. Normally the page with the options of booting from vista or ubuntu would pop up, but now a page saying some stuff about grub and error 22 results instead, and the computer does not boot. I just want to be able boot into Vista again regardless if ubuntu is still on or off my computer. As for unistalling Ubuntu I will worry about that later. If someone could help me I'd be very, very glad.

---

### Post by ronaldprettyman on 2009-07-01
Get a xp or vista disk, go into restore mode.
run 
XP
```
C:\> fixboot
C:\> fixmbr
```
VISTA
```
C:\> BootRec.exe /fixboot
C:\> BootRec.exe /fixmbr
```
Vista Source [http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/](http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/)

---

### Post by atomsmasherr on 2009-07-01
Will try that; Thank you for input

---

### Post by atomsmasherr on 2009-07-01
Because this is the first time I'm doing this I'm not sure of what to do. I loaded the vista disk and was given options, restore being one of them. I tried restoring to an earlier "checkpoint" but once my computer restarts the grub error reoccurs, and so I'm not able to access cmd, Another option other than restore is cmd, but it starts as x:/ instead if C:/, and x:/ does not have Bootrec.exe

---

### Post by ronaldprettyman on 2009-07-01
> **atomsmasherr said:**
> Because this is the first time I'm doing this I'm not sure of what to do. I loaded the vista disk and was given options, restore being one of them. I tried restoring to an earlier "checkpoint" but once my computer restarts the grub error reoccurs, and so I'm not able to access cmd, Another option other than restore is cmd, but it starts as x:/ instead if C:/, and x:/ does not have Bootrec.exe

my bad
```

x:\bootrec /fixboot
x:\bootrec /fixmbr
```
also type help if that doesn't work, will give you a list of commands, look for commands that contain boot mbr, but the above should work

I'm gonna dig up a vista disk and check this real quick
K found a Server 2008 disk(Vista SP1) 
When the disk is boot keep hitting f8,
select safe mode command prompts only(or how ever you can get to a prompt)
Select repair
Select Command Prompt
```

x:\bootrec /fixboot
x:\bootrec /fixmbr
```

---

### Post by atomsmasherr on 2009-07-01
The problem has been fixed and I'm able to boot normally again. You have been tremendously helpful and saved me a great deal of stress and time. Thank you.

---

### Post by ronaldprettyman on 2009-07-01
> **atomsmasherr said:**
> The problem has been fixed and I'm able to boot normally again. You have been tremendously helpful and saved me a great deal of stress and time. Thank you.
Thank the economy :lolflag:
anytime

---

