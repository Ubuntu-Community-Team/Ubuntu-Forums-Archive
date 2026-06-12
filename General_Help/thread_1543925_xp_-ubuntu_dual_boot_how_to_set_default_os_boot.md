---
title: "xp -ubuntu dual boot how to set default os boot?"
date: 2010-08-01
forum: General Help
---

### Post by axxinn on 2010-08-01
I installed ubuntu lucid in a dual boot machine how ca i st the default boot to xp?
i tried the instructions i found on the community docs but it did not work

---

### Post by Dustin2128 on 2010-08-01
grub or wubi?
You'll have wubi if you installed it from within windows, and grub if you booted to the CD and did a full install.

---

### Post by axxinn on 2010-08-01
grub i did install from cd

---

### Post by Dustin2128 on 2010-08-01
> **axxinn said:**
> grub i did install from cd
alright..
first backup your grub file just in case. (sudo is needed to work with any file or directory above /home/user/)
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```then ```
gksudo gedit /boot/grub/menu.lst
```to bring up gedit so you can edit your text file.

Look for this line:
```
default     0

```and replace it with whatever number down windows is on your list, starting from zero and counting every line. (ubuntu, memtest, other os, windows, windows would be 3, not 4).
That should do the trick.

---

### Post by axxinn on 2010-08-01
cp: cannot stat `/boot/grub/menu.lst': No such file or directory
i tried that already the mess above is all i got

---

### Post by prodigy_ on 2010-08-01
The easiest way is to install startup manager: ```
sudo aptitude install startupmanager
```

It's a GUI tool that you can then run from System menu: System/Administration/StartUp-Manager. It allows you to configure some Grub2 settings, including the default menu entry.

---

### Post by axxinn on 2010-08-01
thanks for all your help 
i dont know if i'm doing something wrong  this what the terminal reds
axx@axx-desktop:~$ sudo aptitude install startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "startupmanager"
Couldn't find any package whose name or description matched "startupmanager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

i'm updating the manager now

---

### Post by axxinn on 2010-08-01
thanks a million it is done after i updated the manager i was able to do the start up manager an do the mods thanks again:KS

---

### Post by g00f on 2010-08-01
> **axxinn said:**
> cp: cannot stat `/boot/grub/menu.lst': No such file or directory
i tried that already the mess above is all i got

That's old school Grub v1 configuration file. Chances are you have Grub v2 installed. The file that counts now is /etc/default/grub. You're looking for "set default=0"

Have a read of this [https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2") before you mess with anything.

---

