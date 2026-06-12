---
title: "Permissions for files on cd"
date: 2010-03-05
forum: General Help
---

### Post by Keith1212 on 2010-03-05
Im installing wow from a cd and when i try to open it it says read error. When i check the permissions of the files on the cd it says "503 - user #503". So I don't have the right permissions for some reason. Anyways everytime i try to change permissions it asks for root PW which i do not know. I am very new to ubuntu/linux so any help is appreciated.

---

### Post by Intrepid Ibex on 2010-03-05
What command are you trying to do with wine? Are you even using it?

---

### Post by Red Penguin on 2010-03-05
Hi Keith, hopefully the Howto [here]("http://ubuntuforums.org/showthread.php?t=579378") will be some help.

Kind regards

RP

---

### Post by Keith1212 on 2010-03-05
ty for the replys. Yes i am using wine. When i open the cdrom to view the files i right click to open with wine. I get the read error. Anyways I was using 2 other guides i found so now i have a third to check out. I'll try to figure this out. thanks again. 

Edit as for the link you gave me i can't even do the 2nd part which is copying the files from the disc to a directory since i don't have the permissions. Anyways back to it.

Edit 2 the group is called "dialout".

---

### Post by Keith1212 on 2010-03-05
I'm trying "sudo chown keith  /cdrom/installer.exe" since its the only way it doesn't ask me for root pw. 
then it says "chown: changing ownership of `/cdrom/Installer.exe': Read-only file system"

Then i check the file permissions again and their the same.

---

### Post by Red Penguin on 2010-03-05
Is the sudo password not the same as the one you log in with?

---

### Post by Keith1212 on 2010-03-05
> **Red Penguin said:**
> Is the sudo password not the same as the one you log in with?
yea when i sudo i put in the pw for my account "keith". it takes it then just says "chown: changing ownership of `/cdrom/Installer.exe': Read-only file system" yet the file is unchanged. i tired chown, chmod, and chgrp with no luck.

Edit i'm just gonna dl the install files thx anyways guys.

---

### Post by lyall on 2010-03-05
files on CDs/DVDs are read only
the reason why they are is because the data is burned to the CD/DVD
and you can not re-write to then at the same location that the data was burnt to

CD/DVD-RW are different.  You first have to format them, then you can write and delete file/s

good luck and have fun learning

---

### Post by Bulletb on 2010-04-08
I am having this same issue.  When trying to install WOW from DVD's, the first two (Original & Burning Crusade) worked fine after the files were unhidden.  However, when I tried the Lich King DVD, the files come up as having no access for me.  I am using the only account on this computer.  Just like the original post, the files on the DVD say user 503.  I can not copy them, open them, or run them.  Is there any way to fix this?  I am fairly new to Ubuntu/Linux so I do not know many of the low level commands yet.

Currently running: Ubuntu 9.10 with & wine version 1.1.41

---

