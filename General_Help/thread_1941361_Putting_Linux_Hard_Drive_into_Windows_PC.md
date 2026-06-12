---
title: "Putting Linux Hard Drive into Windows PC"
date: 2012-03-15
forum: General Help
---

### Post by curiousnoob on 2012-03-15
I just got a new Windows 7 PC and had an old HDD with lots of data on it that I installed into it as a second drive.  
I quickly realized that I had forgotten that Linux uses the ext system so even though Windows recognizes the drive I can't access the info.  
I think the best solution would be to transfer all the data from the old linux drive to the new windows drive then format the old one but I have no idea how to access the data from within windows. 
Anyone have any ideas/clever workarounds?

---

### Post by sudodus on 2012-03-15
Run a live session, you need not install Ubuntu.

One way is to make a boot CD or USB drive from a downloaded [KLX]Ubuntu installation iso file. Then you can boot your computer into linux and access both file systems, so that you can transfer any files you like from your ext file system to your ntfs file system.

*Nota bene*: the file permissions will not be preserved, but that is no problem for regular data files.

---

### Post by forrestcupp on 2012-03-15
You can also install [Ext2Read](http://sourceforge.net/projects/ext2read/) in Windows, and if you have administrator rights, you'll be able to view and copy your ext partitions.

---

### Post by goldshirt9 on 2012-03-15
[http://www.linuxjournal.com/article/9449](http://www.linuxjournal.com/article/9449)
if any use

---

### Post by curiousnoob on 2012-03-15
> **forrestcupp said:**
> You can also install [Ext2Read](http://sourceforge.net/projects/ext2read/) in Windows, and if you have administrator rights, you'll be able to view and copy your ext partitions.

OK, stupid question.  
How do I run a program as the admin? Logged in the only user available.
Nevermind.  Figured it out.

---

### Post by miegiel on 2012-03-15
Nothing wrong with the suggestions above, but you can also try booting the linux on your old hard drive.

(Get into your BIOS and tell it to boot the other disk)

---

### Post by 2F4U on 2012-03-15
If I am not mistaken, you right click on the program and select "Run as Administrator".

---

