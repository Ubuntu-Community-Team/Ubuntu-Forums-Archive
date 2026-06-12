---
title: "help with grub menu list"
date: 2009-10-01
forum: General Help
---

### Post by bonowantbiddy on 2009-10-01
I was editing my grub boot list and accidentally put a # for ubuntu so it does not appear on the list anymore, there for i cannot reboot and change it. is there any way to edit the menu.lst file? i really dont want to reinstall.

thanks

---

### Post by scragar on 2009-10-01
From a liveCD you will be able to mount your partition and edit the file.

---

### Post by bonowantbiddy on 2009-10-01
> **scragar said:**
> From a liveCD you will be able to mount your partition and edit the file.

thanks for the quick response, but im not sure how to do mount it properly.....im a linux noob

---

### Post by scragar on 2009-10-01
LiveCDs after 8.04, I think, will list it in the places menu, otherwise you'd have to mount it manually:
```
sudo fdisk -l
```Will show partitions and disks available, if you can tell which partition you want to mount you can do:
```
sudo mkdir /media/foo
sudo mount /dev/**sda1** /media/foo
```
To mount it.

---

### Post by mikehenson on 2009-10-01
Boot into Ubuntu Live and goto Places -> "XXX GB Media" 
goto terminal and type:
```
sudo gedit /media/disk/boot/grub/menu.lst
```
This should bring up your menu.lst file
MSH

---

### Post by bonowantbiddy on 2009-10-01
> **scragar said:**
> LiveCDs after 8.04, I think, will list it in the places menu, otherwise you'd have to mount it manually:
```
sudo fdisk -l
```Will show partitions and disks available, if you can tell which partition you want to mount you can do:
```
sudo mkdir /media/foo
sudo mount /dev/**sda1** /media/foo
```To mount it.

Okay got that, but when i open the menu ls file its completely empty. Running as root has the same result. This cant be right tho because the boot loader shows the memorytest option on boot.

---

### Post by mikehenson on 2009-10-01
> **bonowantbiddy said:**
> Okay got that, but when i open the menu ls file its completely empty. Running as root has the same result. This cant be right tho because the boot loader shows the memorytest option on boot.

Your menu.lst should then be in
/media/foo/boot/grub/menu.lst
NOT
/boot/grub/menu.lst

MSH

---

### Post by oldfred on 2009-10-01
If it was empty then you did not have the correct path or a typo on the name.

another way to open it:
The easiest way to edit your files is to boot with the live CD.

Use Naulitus/file browser, places, computer, find your filesystem, drill down thru /boot/grub so you can see menu.lst. Do not double click as it will not let you save it but right click, choose open with, in the open with window scroll to the bottom Open with other Application, at bottom where it says use other application, click on it and it will open a single line, type in gksudo gedit and it will open the file in superuser mode so you can save it. It may seem long but is easy once you right click and scroll down.

---

### Post by bonowantbiddy on 2009-10-01
> **mikehenson said:**
> Your menu.lst should then be in
/media/foo/boot/grub/menu.lst
NOT
/boot/grub/menu.lst

MSH

found it! thanks a million!!!!!

---

