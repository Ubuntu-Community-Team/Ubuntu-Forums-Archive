---
title: "Grub...dead. Or at least paralyzed"
date: 2005-03-03
forum: General Help
---

### Post by Adrenal on 2005-03-03
I was recently trying to add a grub splash picture. Inherently, however, i did something wrong, and now grub doesn't seem to want to boot. I followed the directions from [this](http://sleepybuddha.sl.funpic.de/ubuntu/)  page, but i must of done something wrong.
Please help me, is there any way to repair gaim. That is, set it back to its default settings, or restore it?
Thankyou in advance

---

### Post by rkn on 2005-03-03
You can repair the file.
Boot with CD.
Create a mount directory and Mount your partition where the grub files are located.
Example:
[COLOR=Blue]mkdir /mnt/temp
mount /dev/hda1 /mnt/temp[/COLOR]
Open the file to edit:
[COLOR=Blue]vi /mnt/temp/boot/grub/menu.lst[/COLOR]

Online manual for Grub is here:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Bob

---

