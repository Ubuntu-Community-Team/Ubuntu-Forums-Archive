---
title: "Removing kernels from grub"
date: 2010-08-16
forum: General Help
---

### Post by mac67 on 2010-08-16
Hello! I hope I am in the right forum.

I have just upgraded to Kubuntu 10.4, dual boot with Windows Vista.

Last time I run Start-Up Manager in order to change default boot, an external hard disk, that I use as file archive, was connected via USB. This HD also contains Xubuntu 9.10 in one partition. As a result, during boot Grub2  shows also the kernels of the external HD.

Two questions:

1) Might that cause problems?
2) How can I remove these two Xubuntu kernels from Grub?

Thank you!

---

### Post by mac67 on 2010-08-18
Too difficult a question? Nobody can help me?

---

### Post by Ad@m on 2010-08-18
It should not create any problems.

Run the command update-grub as root, this will automatically update your grub.cfg file.

> sudo update-grub

---

### Post by worksofcraft on 2010-08-18
Reason a new install leaves the old kernels there is just in case your upgrade fails. Once you are happy that it's all ok it is a good idea to remove the old kernels.

Update-grub does not remove anything it simply updates the boot menu to have entries for all the operating systems it can find.

Last time I upgraded I used System Janitor, or maybe it was synaptic package manager to remove the obsolete ones. Recently there was a thread where I read about ubuntu-tweak that does a much better job... check it out: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

oh.... and after you removed them, only then run "update-grub" to update the grub menu and remove the obsolete entries ;)

---

### Post by Ad@m on 2010-08-18
> **worksofcraft said:**
> 

Update-grub does not remove anything it simply updates the boot menu to have entries for all the operating systems it can find.



If he runs update-grub with the external disconnected it wont find the xubuntu kernels.

[https://wiki.ubuntu.com/Grub2#Removing%20Entries%20from%20Grub%202](https://wiki.ubuntu.com/Grub2#Removing%20Entries%20from%20Grub%202)

"Other operating systems which have been removed from the computer will also be removed from the menu once "update-grub" is run as *root*. "

---

### Post by mac67 on 2010-08-18
> **Ad@m said:**
> It should not create any problems.

Run the command update-grub as root, this will automatically update your grub.cfg file.

Shame on me...#-o

I had tried to update with the Start-up Manager, but I failed, and I supposed that update-grub was the same and not worth a try.

Thank you Ad@m!

---

