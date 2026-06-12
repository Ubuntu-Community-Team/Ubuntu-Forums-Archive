---
title: "boot screen"
date: 2009-12-15
forum: General Help
---

### Post by mIXpRo on 2009-12-15
hii,
 
 I've installed ubuntu jaunty (9.04) , I'm using it and its great .
but every once in while at the boot screen (when you asked to select the operating system) it adds a row saying ubuntu recovery , and another one for ubuntu regular .
how can i remove them ?

---

### Post by pi4r0n on 2009-12-15
Edit grub file by doing 

> vi /boot/grub/menu.lst 


and on the bottom of the file # recovery and others :)

---

### Post by drs305 on 2009-12-15
For grub legacy, a GUI app called StartUpManager has the option to permanently inhibit the display of the recovery mode options. 

I wrote a guide about it a while back that will tell you how to install and run SUM. Click the "SUM" link in my signature line. The recovery mode display option is in the "Advanced" tab section.

StartUpManager can tweak a lot of Grub legacy settings. For users with Grub 2, some SUM settings work and some don't. My Grub 2 guides discuss hiding the Recovery mode in G2.

---

### Post by drs305 on 2009-12-15
For grub legacy, a GUI app called StartUpManager has the option to permanently inhibit the display of the recovery mode options. 

I wrote a guide about it a while back that will tell you how to install and run SUM. Click the "SUM" link in my signature line. The recovery mode display option is in the "Advanced" tab section. StartUpManager has a variety of tweaks that can easily be made without manually editing the menu.lst system file.

For Grub 2, the line to edit is 
> GRUB_DISABLE_LINUX_RECOVERY="true"

See the Grub 2 Basics link below for more details about this option.

---

### Post by mIXpRo on 2009-12-15
[pi4r0n]("http://ubuntuforums.org/member.php?u=875951")
it won't let me

---

### Post by drs305 on 2009-12-15
> **mIXpRo said:**
> it won't let me

You may have to be more specific, but editing the menu.lst file, either via vi or another text editor, or via StartUpManager, requires administrative rights since it is a system file.

If you are using gedit, use "gksudo gedit /boot/grub/menu.lst". If you are using vi, start it with "sudo vi". And if you are using StartUpManager, you will be asked for you password when you start it from the menu (or "gksudo startupmanager").

---

### Post by mIXpRo on 2009-12-15
thank you drs305 pi4r0n problem solved .
you really know these things ;).

---

### Post by pi4r0n on 2009-12-16
> **mIXpRo said:**
> [pi4r0n]("http://ubuntuforums.org/member.php?u=875951")
it won't let me

Sorry **mIXpRo;8503506** I thought you know that you need to use **sudo** :) as its restricted file and is only allowed to be viewed by root:)

> sudo vi /boot/grub/menu.lst

enter root password and then job done

---

