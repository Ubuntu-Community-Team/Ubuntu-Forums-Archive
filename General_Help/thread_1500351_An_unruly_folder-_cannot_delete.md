---
title: "An unruly folder- cannot delete"
date: 2010-06-03
forum: General Help
---

### Post by krishnamohan on 2010-06-03
Hi....

I have a folder which seems to have got corrupted...I cannot see the contents...I cannot copy any files into it...

I tried rm -r on that folder...but it says that cannot be deleted..not empty....

I tried to delete the folder from windows also..and got the same reply...

What can be done?

---

### Post by Spr0k3t on 2010-06-03
You can see the directories on the windows side?  What's the filesystem on the drive?  Also, have you tried scanning for bad sectors on the drive?

---

### Post by Rubi1200 on 2010-06-03
Have you checked the folder permissions?

---

### Post by efflandt on 2010-06-03
What does **ls -al foldername** show?  Have you tried using **sudo**, to remove it as root.  Just be [COLOR=Red]very[/COLOR] careful about using the correct foldername when you do that, and avoid using wildcards (*)?

---

### Post by bumanie on 2010-06-03
Try > kdesu konquerer in terminal. This should put you in to graphical mode with root permissions - you should be able to navigate to the folder and delete it, but remember you are in admin mode, so double check you are deleting the correct thing before deleting it.

---

### Post by -humanaut- on 2010-06-03
Wheres the file at?

---

### Post by krishnamohan on 2010-06-08
I had tried to remove it as root..but did not work....

But now when I check, I see that the folder is back to normal!...I can see the contents..I can send it to trash...I can copy files into it....

I was going to scan for bad sectors and then thought will try

ls -al folder

It showed me the contents...I then checked through the GUI...and everything is fine...I do not know how...unless computers have developed AI and started using surreptitious techniques to test human response to vagaries in computer behaviour...

Thanks for your replies....:p.....sorry for the late response..been travelling for a couple of days...

---

