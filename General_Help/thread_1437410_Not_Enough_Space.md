---
title: "Not Enough Space?"
date: 2010-03-23
forum: General Help
---

### Post by ryandyke on 2010-03-23
I am new to the ubuntu community, but when I tried installing a game with wine it said i didnt have enough space when I know that I have at least 300 gigs free on my hard drive. Pls help (see pic)

---

### Post by 3rdalbum on 2010-03-23
It doesn't matter how much space is available on other hard disks; you need to have that space available in your home directory (which is where Windows programs get installed). You've just provided us with a screenshot of two NTFS partitions, which makes me think you've installed Ubuntu using the Windows-based installer - this actually installs Ubuntu within a file on your hard disk. You'd need to have that 2 gigabytes of free space in the file in order to install your program.

The Windows-based Ubuntu installer limits you to 30 gigabytes of Ubuntu space (or, of course, less if that's what you chose). If you want to keep Ubuntu, you should probably boot up your computer from the Ubuntu CD and install Ubuntu by repartitioning the hard disk; the Ubuntu installer will help you with this. Maybe partition it so that you've got 100 gigabytes allocated?

---

### Post by louieb on 2010-03-23
Look like you did a WUBI install of Ubuntu. It can only use the space you gave it at time of  install.  

Haven't used WUBI - don't know much about it. Take a look at the [WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide")

Welcome to Ubuntu forums.

---

### Post by ppirilla on 2010-03-23
open a terminal and run the command "df -h".  That should tell you exactly how much space you have where.

---

