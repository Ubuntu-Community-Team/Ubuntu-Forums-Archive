---
title: "Removing root from folder...???"
date: 2010-07-15
forum: General Help
---

### Post by robertcoulson on 2010-07-15
Hi...Used TESTDISK to retrieve pictures from my 16 gb stick...Copied all folders from the retrieved files to a new folder for burning later...Went back to delete rescued pictures in folders and there is a LOCK on ALL pics and document...Can not delete them...WHY...??? (see attachment)
Robert

---

### Post by Hanzerik on 2010-07-15
> **robertcoulson said:**
> Hi...Used TESTDISK to retrieve pictures from my 16 gb stick...Copied all folders from the retrieved files to a new folder for burning later...Went back to delete rescued pictures in folders and there is a LOCK on ALL pics and document...Can not delete them...WHY...??? (see attachment)
Robert

Are you trying to delete the folders/pictures from the thumb-drive or a folder in your HOME or Desktop?

---

### Post by emoguitarist06 on 2010-07-15
Somehow the files were copied over with root permision

the easiest why i've found is to press ALT + F2 type "gksudo nautilus" type password and then navigate to that folder and you'll be able to delete with root permission

---

### Post by Hanzerik on 2010-07-15
> **emoguitarist06 said:**
> Somehow the files were copied over with root permision

the easiest why i've found is to press ALT + F2 type "[COLOR="Red"]gksudo[/COLOR] nautilus" type password and then navigate to that folder and you'll be able to delete with root permission

I always forget about that command...I usually just open a terminal and either "sudo su -" and work as root, or just use "sudo <command>".

---

### Post by robertcoulson on 2010-07-15
OK..typed in " gksudo nautilus " like you said and went to that folder to delete the files and it would not give me permission.
Robert

---

### Post by prodigy_ on 2010-07-15
Hmm. Why don't you just format the stick?

---

### Post by robertcoulson on 2010-07-15
Yikes...Thats what I have been trying to do, but nothing allows me to format it..Get a superblock error and when I used TESTDISK to retrieve all the pictures, it put these locked files under ROBERT which I think is my root folder..Does that make any sense...???
Robert

---

### Post by tsx2424 on 2011-05-08
> **emoguitarist06 said:**
>  
the easiest why i've found is to press ALT + F2 type &quot;gksudo nautilus&quot; type password and then navigate to that folder and you'll be able to delete with root permission

  Thanks for help.

---

### Post by rickyclarke15 on 2011-05-08
I had Win Me, i placed a photo in the root folder of one of my drives  like "F:\"   then i upgraded to Win Xp, but now i can't remove the photo  that found in the root folder of my Drive.

---

