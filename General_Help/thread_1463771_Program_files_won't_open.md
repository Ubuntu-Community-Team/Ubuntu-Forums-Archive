---
title: "Program files won't open"
date: 2010-04-27
forum: General Help
---

### Post by Silent_Voice on 2010-04-27
I have both Windows and Ubuntu on my laptop and I need to access the windows program files via Ubuntu (windows don't start). The problem is that the program files folder  appears to be empty. Is there any way to retrieve data from ubuntu?

---

### Post by viralmeme on 2010-04-27
> **Silent_Voice said:**
> I have both Windows and Ubuntu on my laptop and I need to access the windows program files via Ubuntu (windows don't start). The problem is that the program files folder  appears to be empty. Is there any way to retrieve data from ubuntu?
Mount the Windows partition as root. What does df -h say?

---

### Post by Silent_Voice on 2010-04-27
I'm sorry if this wasn't understood from my post but I can navigate in the Windows partition with no problem at all, all the files are where they are suposed to be. Except from the program files folder, when i double click it, the system lags for a second and then opens with no folders in it. The same with the navigation through terminal. Also there are no hidden files.

---

### Post by Silent_Voice on 2010-04-29
Anyone ideas?

---

### Post by zoeker on 2010-04-30
I have the same problem but the directories that appear to be empty are Documents and Settings, Program Files and Windows. Anyone got a hint what might be wrong with these?

---

### Post by Silent_Voice on 2010-05-04
When I navigate in terminal in Program Files and hit ls it shows "ls: reading directory .: Input/output error".. I hope that does help...

---

### Post by WorMzy on 2010-05-04
Did you resize any partitions when you installed Ubuntu?

---

### Post by Silent_Voice on 2010-05-05
I'm pretty sure I didn't...

---

### Post by dino99 on 2010-05-05
is the windows bootloader erased ?
are they real install or with virtualbox ?

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Silent_Voice on 2010-05-10
I use grub as a bootloader..
Windows are actually installed, no virtualbox or anything..
About the guide there is no problem about mountibg the windows partition in ubuntu, it is absolutely normal except fot the program files folder...
Thanks for your reply.

---

### Post by Silent_Voice on 2010-05-26
Sooooo anyone has any idea??

---

