---
title: "Wine is looking in the wrong partition for programs..."
date: 2010-09-26
forum: General Help
---

### Post by PPM5895 on 2010-09-26
Hey everyone. :D
I've finally gotten around to installing Wine. But I have a problem. My computer has 3 partitions. It has a 7gb Win95-NT partition, a 70gb WinXP partition, and a 23gb Ubuntu partition. 

Wine is looking for programs in the 95-NT partition, so all it finds is Notepad. :/

Is there any way for me to tell it to look in the XP partition?

Thanks in advance. :3

---

### Post by Darkness Des on 2010-09-26
Wine isn't looking for programs in any of your windows partitions. It's looking in the hidden folder *.wine*, which is located in your home folder.

---

### Post by gandaran on 2010-09-26
wine uses its own drive C located in home user .wine folder and yes notepad is the only installed application until you install more.

---

### Post by PPM5895 on 2010-09-26
:/ 
Is there any way to make it get programs I already have installed? Not looking forward to reinstalling Adobe CS. >______>

Ah. Thanks Gandaran and Des. ^_^

---

### Post by Darkness Des on 2010-09-26
There is always the option of making a symbolic link, OR you could just copy the program files directory over.

---

### Post by PPM5895 on 2010-09-27
Something might be wrong then. I linked to Adobe CS4 from the program files folder in the XP partition and put it in the program files folder on Wine. The folder appeared to be totally empty. :/
Did I do something wrong?

---

### Post by Darkness Des on 2010-09-28
Did you create the link on Windows?

---

### Post by PPM5895 on 2010-09-28
Nope. I made it in Ubuntu. Wrong move I assume? :p
I'll try making the link from Windows and see if that fixes it. :D

---

### Post by Darkness Des on 2010-09-29
Actually, doing it on Ubuntu was the right move. I'm just not sure if the file browser makes precisely the kind of links we want. What we want is a symbolic link. What I think that the file browser is doing is creating .desktop files (the same as a Windows) shortcut, which tell it open that file or folder. A Symbolic link basically tells the computer that the file/folder IS located there, but it just needs to go to another spot to see it. It's effectively the same as making a copy of something, but  it doesn't take up any extra space. The only downside is that the original copy has to exist and cannot be placed elsewhere if you want the link to work.

---

