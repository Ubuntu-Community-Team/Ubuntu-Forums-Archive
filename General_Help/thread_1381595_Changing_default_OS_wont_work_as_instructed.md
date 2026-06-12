---
title: "Changing default OS wont work as instructed?"
date: 2010-01-14
forum: General Help
---

### Post by talkingtree on 2010-01-14
Hi,

I'm doing everything exactly as described in [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

But when I get to the backup setting section, I got this on my terminal

```
charlieubuntu@charlieubuntu:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
[sudo] password for charlieubuntu: 
cp: cannot stat `/boot/grub/menu.lst': No such file or directory

```

And when it says to open a menu.lst in a text editor, I went to Application->Accessories->gedit Text editor, I cant find menu.lst?

---

### Post by Jackzor on 2010-01-14
If you are using grub2 then this will not work for you. I believe that the tut the you found is for grub legacy.

---

