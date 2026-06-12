---
title: "dual os"
date: 2010-08-10
forum: General Help
---

### Post by Manikris on 2010-08-10
Hi 
I am new to Linux . I am having win 7 in my laptop in /dev/sda1. I installed ubuntu in /dev/sda2 ..
When i power on my machine , i dont get a dual boot option , i am directly taken to win 7.
When i tried fdisk -l with help of a live cd of ubuntu , i find that /dev/sda1 is bootable ...

What should i do to get a dual boot option ?

---

### Post by Manikris on 2010-08-10
anyone please help ...

---

### Post by TNT1 on 2010-08-10
edit the mbr of the windows partition?

---

### Post by azertyh on 2010-08-10
hi,
the documentation about [grub]("https://help.ubuntu.com/community/Grub2") can help you i think.

---

### Post by stinkeye on 2010-08-10
[**_[COLOR="DarkRed"]How to restore the Ubuntu/XP/Vista/7 bootloader[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1014708")

In the terminal run **sudo fdisk -l** to check that [COLOR="#ff00ff"]sda2[/COLOR] is the partition where you installed Ubuntu.

From the above tutorial(using your fdisk -l result) boot into a live cd and
```
sudo mkdir /media/[COLOR="Magenta"]sda2[/COLOR]
sudo mount /dev/[COLOR="#ff00ff"]sda2[/COLOR] /media/[COLOR="#ff00ff"]sda2[/COLOR]
```

```
sudo grub-install --root-directory=/media/[COLOR="#ff00ff"]sda2[/COLOR] /dev/[COLOR="DarkOrange"]sda[/COLOR]
```
[COLOR="Magenta"]Change for your ubuntu partition.[/COLOR]
[COLOR="#ff8c00"]Change for the **drive** (not partition) where Windows is installed[/COLOR]

---

### Post by elliotn on 2010-08-10
Reinstall grub

---

