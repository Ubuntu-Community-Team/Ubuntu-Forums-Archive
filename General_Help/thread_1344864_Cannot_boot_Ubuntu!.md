---
title: "Cannot boot Ubuntu!"
date: 2009-12-03
forum: General Help
---

### Post by ShinIori319 on 2009-12-03
Hello.
I'm pretty new with Linux at all. I decided to install Ubuntu using Wubi in my drive C:\. The first times, Ubuntu managed to boot without any issues, but after the kernel upgraded via the Update managed, Grub boot loader will not recognize any of my installed systems (Vista bootloader does without problems).
Instead of the OS selection menu, I get a console-like screen with this:
 
**[COLOR=red]sh:grub>[/COLOR]**
**[COLOR=#ff0000][/COLOR]** 
[COLOR=black]Can someone help me in getting my Ubuntu installation back?[/COLOR]
Thanks in advance.

---

### Post by Chame_Wizard on 2009-12-03
If you have a partition with free space,you can install Ubuntu on it.

You have GRUB installed and you can use the newest kernels without any problem.:guitar:

---

### Post by ShinIori319 on 2009-12-03
> **Chame_Wizard said:**
> If you have a partition with free space,you can install Ubuntu on it.
 
You have GRUB installed and you can use the newest kernels without any problem.:guitar:
 
 That's what I don't want to do for now. I used Wubi mainly so I don't have to mess with the partitions right now. I may do that once I get some experience with Linux.

---

### Post by Eremis on 2009-12-03
Exit out of grub, and get on a regular command line. (I think ctrl-c) then from there reinstall grub. 
1. ```
sudo apt-get remove grub
```
2. ```
sudo apt-get install grub
```
3. Then edit the entries (But make sure u know the name where windows,and linux is... where hd0, hd1...etc it is)

---

### Post by ShinIori319 on 2009-12-03
> **Eremis said:**
> Exit out of grub, and get on a regular command line. (I think ctrl-c) then from there reinstall grub. 
1. ```
sudo apt-get remove grub
```
2. ```
sudo apt-get install grub
```
3. Then edit the entries (But make sure u know the name where windows,and linux is... where hd0, hd1...etc it is)
 
 
Nope, it did not work. I got out of GRUB and the computer rebooted. I think I'll reinstall Wubi from scratch.

---

### Post by Oriol Gordó on 2009-12-05
I had a similar problem. I've found the solution in another thread:

[http://ubuntuforums.org/showthread.php?p=8447380&posted=1#post8447380](http://ubuntuforums.org/showthread.php?p=8447380&posted=1#post8447380)

I hope that could be useful.

---

### Post by ShinIori319 on 2009-12-05
> **Oriol Gordó said:**
> I had a similar problem. I've found the solution in another thread:
 
[http://ubuntuforums.org/showthread.php?p=8447380&posted=1#post8447380](http://ubuntuforums.org/showthread.php?p=8447380&posted=1#post8447380)
 
I hope that could be useful.
 
Thanks, I'll try doing that if this happens again. :) I think I'll make a backup of the Wubi installation just in case this or a Kernel panic happens. (I've had this problem as well lately)

---

