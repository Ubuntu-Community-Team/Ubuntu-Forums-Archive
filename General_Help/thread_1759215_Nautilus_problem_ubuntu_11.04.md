---
title: "Nautilus problem ubuntu 11.04"
date: 2011-05-15
forum: General Help
---

### Post by kadlam on 2011-05-15
**Nautilus problem in ubuntu 11.04** 			
 			 			 		   		 		 		I recently upgraded and now having problems with nautilus. 
1) I don't know for sure if it's related but all of the icons on my  desktop (files located in desktop) have little lock symbols in the upper  right-hand corner of the icon. 
2) I cannot open files from the desktop (because they are evidently locked)
3) I cannot open any of the folders listed when I go to "Places" (between Applications and System top of the screen)

Running nautilus from the terminal, I CAN go to different folders and open files in the usual manner. 

Any ideas why I'm having the troubles from desktop?

Thanks,
Ken

---

### Post by kadlam on 2011-05-15
NOTE TO SELF

I believe I understand now. The padlock symbol occurs on the folders / files that I copies from the CD. I didn't realize at the time that these would be owned by root. I shall now attempt to change ownership and see if that resolves the problem.

---

### Post by kadlam on 2011-05-16
ANOTHER NOTE TO SELF - nothing resolve
the problem is larger than I thought

---

### Post by kadlam on 2011-05-18
FINAL NOTE TO SELF ON THIS SUBJECT
 
After spending way too much time on the problems I decided to re-install Ubuntu 11.04. Here's what I learned in the experience:
 
Be careful when copying files and directories from a CD. In my case, I thought it would be time-saving to simply copy the /home directory from my previous set-up to the new one. Bad idea. It's best to leave the newly set-up /home directory in place and then just add to it as one normally would. 
 
This time around, I simply copied what I wanted from the CD to a temporary folder and didn't try to mess with the /home directory that was automaticlaly set up when installing 11.04. 
 
Files transferred from a CD evidenly default priveldges to root and those scripts and such that were previously executable lose that capability as well. So, for example, files that I had previously on my desktop now would show up as being locked (an icon on teh desktop with a small padlock in the upper right-hand corner).  Using recursive chmod it was easy enough to change all these to the permission level I desired. 
 
There's more but that's all for now.

---

### Post by Hedgehog1 on 2011-05-19
NOTE TO kadlam:

I had a professor who always said we learn the most when we break things.  I was taking microprocessor design at the time (fun class) and I sure broke a lot of things.

The command **chown** (**CH**ange **OWN**er) can be a help at times like these.

Also, if you store your '/home' in its own partition, you can make upgrades/reinstalls/downgrades a lot less painful.

Here is an example:

If you have your data in a separate '/home' partition you can install 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by kadlam on 2011-05-20
Hedge:
Thanks so for the information. I know what my homework assignment is for the weekend. 
Very much appreciated.

---

