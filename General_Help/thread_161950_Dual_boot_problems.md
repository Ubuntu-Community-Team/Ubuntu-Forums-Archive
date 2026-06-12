---
title: "Dual boot problems"
date: 2006-04-18
forum: General Help
---

### Post by Bilbo Tubbins on 2006-04-18
ok so i got ubuntu on and somehow have managed to no put xp in grub.:-k

---

### Post by Sutekh on 2006-04-18
Are you in Ubuntu now?

Can you supply the output from these commands
```
sudo fdisk -l
```
 - Use your user's password when prompted
 - This command will list all your partitions, so we will know where Ubuntu/Windows are

```
cat /boot/grub/menu.lst
```
 - This will print the GRUB menu to the screen
 - This file is where you can tell GRUB how to boot Windows XP

 - If you have multiple hard drives, then this command may also help
```
cat /boot/grub/device.map
```
 - It lists the way GRUB numbers the hard drives

---

### Post by pwrstick on 2006-04-18
[QUOTE=Bilbo Tubbins]ok so i got ubuntu on and somehow have managed to no put xp in grub.:-k[/QUOTE]

alternatively, you can copy:
```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

into your menu.lst file located /boot/grub/ 

I had your problem once and simply copied this from someone else.  Of course, the (hd0,0) may have to be changed to match which drive/partition your XP is on.

---

### Post by Bilbo Tubbins on 2006-04-18
ok did that and got an error code 12

---

### Post by Bilbo Tubbins on 2006-04-18
my ntfs partition comes up as sda 5 if thats any help

---

### Post by Sutekh on 2006-04-18
[quote=Bilbo Tubbins]my ntfs partition comes up as sda 5 if thats any help[/quote]That will help.  What about the output from the device.map?

I would suggest (without seeing that file) that you need an entry like this
```
title           Microsoft Windows XP Professional
root            (hd0,4)
savedefault
[B]map           (hd0,0) (hd0,4)
map           (hd0,4) (hd0,0)[/B]
chainloader     +1
```
The key is the **map** commands.  This will fool Windows into thinking that it resides on the first partition of the first disc.  In case you were wondering the GRUB menu counts from 0, so sda5 is (hd0,4), but this also depends on the contents of the deivce.map

---

### Post by Bilbo Tubbins on 2006-04-18
getting the same error message, partitions availible or something and then 0x7

---

### Post by Bilbo Tubbins on 2006-04-18
the error i get is filesystem type unknow, partition 0x7

---

