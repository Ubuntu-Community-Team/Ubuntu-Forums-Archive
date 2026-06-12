---
title: "Which file system for Ubuntu 9.10 ?"
date: 2009-10-25
forum: General Help
---

### Post by simartem on 2009-10-25
There are 2 partitions on my HDD, on partition #1, there is Ubuntu 9.0.4 which I am using right now. _The file system on partition #1 is NTFS._

There is 25 gigabytes available on partition #2, but i haven't formatted it yet. I want to install 9.10 on this partition number #2. _Which file system should i prefer_ ? I dont know anything about ext2, ext3 and ext4 ? I need some professional assistance. Thank you.

---

### Post by shadow120 on 2009-10-25
ext4 is the default on 9.10 i dont think there is much difference between ext3 and ext4

---

### Post by simartem on 2009-10-25
will there be any conflicts or issues, if i format the second partition with ext4 ? Because the other partition is NTFS on the same HDD

---

### Post by shadow120 on 2009-10-25
i dont think it would be any different that a dual boot witch uses both on the same hd

---

### Post by ranch hand on 2009-10-25
> **simartem said:**
> will there be any conflicts or issues, if i format the second partition with ext4 ? Because the other partition is NTFS on the same HDD
No.

---

### Post by rockstarrem on 2009-10-25
Go with ext4, everything will be fine.

---

### Post by simartem on 2009-10-25
> **rockstarrem said:**
> Go with ext4, everything will be fine.

ok. thank you.. but there is one more question..

I have 2 Internal HDD.. 

on HDD #1 - Windows XP is installed..
on HDD #2 (partition 1) - Ubuntu 9.0.4 is installed
now i will install
on HDD #2 (as partition 2) - Ubuntu 9.10

I have a menu when computer starts, it lets me choose the OS, but if i dont make a choice, automatically windows xp starts.. How will i be able to make this menu with 3 options ?

---

### Post by rockstarrem on 2009-10-25
I believe you need to edit menu.lst. It's quite complicated and I thought GRUB did this automatically, but if it doesn't: [http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/](http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/)

---

### Post by simartem on 2009-10-25
I am not sure but i feel as if i would have to make some settings under windows, because i saw some settings about boot menu, in msconfig.. My primary boot partition is on HDD #1.

---

### Post by DeMus on 2009-10-25
> **simartem said:**
> I am not sure but i feel as if i would have to make some settings under windows, because i saw some settings about boot menu, in msconfig.. My primary boot partition is on HDD #1.

When you install 9.10 it will create a new Grub menu list for you. Don't worry. You will see all your systems, ready to be chosen.

---

