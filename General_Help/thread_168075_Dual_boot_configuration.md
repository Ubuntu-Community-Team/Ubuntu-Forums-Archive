---
title: "Dual boot configuration????????"
date: 2006-04-29
forum: General Help
---

### Post by PoyBoy on 2006-04-29
I have a dual boot with Windows XP home, and Breezy Badger (gnome), and as the default, ubuntu boots up.  This is annoying as I need windows for school at this point, and would like to know how to make windows the default.



Thanks.

---

### Post by bluevoodoo1 on 2006-04-29
[http://www.ubuntuforums.org/showthread.php?t=84373&highlight=boot+order#4](http://www.ubuntuforums.org/showthread.php?t=84373&highlight=boot+order#4)

---

### Post by ncappel1 on 2006-04-29
you need to edit your menu.lst file in /boot/grub and change the default load option. the default is 0, but it could be set to 1. change the option to the number that windows is.

the list is usually 
ubuntu kernal number x.x.x
ubuntu memtest
another ubuntu kernal
whatever windows is


in this case to use windows the default number to load would be "4"

make sense?

---

### Post by cilynx on 2006-04-29
Read / Edit your /boot/grub/menu.lst

The "default" value at the top is what you're looking for.
Setting it to "saved" may be a good idea as it lets you define the default from the grub menu in the future instead of having to edit the file again.

---

