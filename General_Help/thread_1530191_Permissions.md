---
title: "Permissions"
date: 2010-07-13
forum: General Help
---

### Post by AJ4PH on 2010-07-13
Why is it that anytime I try to save anything to a harddrive I get a message that says the folder cannot be copied because you do not have permissions to create it in the destination? Is there some way to get around this? I like Ubuntu but this is getting really annoying.

---

### Post by nothingspecial on 2010-07-13
You can use ```
gksudo nautilus
``` to do it graphically

```
sudo cp
``` to do it in the terminal

or change the drives permissions if it supports linux permissions 

or use fstab to mount it read write if it doesn`t

---

### Post by deathadder on 2010-07-13
> Why is it that anytime I try to save anything to a harddrive I get a message that says the folder cannot be copied because you do not have permissions to create it in the destination? Is there some way to get around this? I like Ubuntu but this is getting really annoying.
Is this a external or internal hard drive? What file system is it? How are you mounting it?

---

### Post by Roasted on 2010-07-13
> **AJ4PH said:**
> Why is it that anytime I try to save anything to a harddrive I get a message that says the folder cannot be copied because you do not have permissions to create it in the destination? Is there some way to get around this? I like Ubuntu but this is getting really annoying.

Once you set the permissions, you shouldn't have to worry about this any longer. This is what you call "security." Even if it feels like a pain, just think about the added level you're getting.

---

### Post by WorMzy on 2010-07-13
You, as a user, can only save files to your home folder by default. If you need to edit a system textfile, open it with gksu gedit (graphical), or sudo nano (terminal).

If you want to move a file to the system directories, use the methods nothingspecial suggested.

If you want to mount an ntfs partition, add an entry in fstab for it with the options to mount it with permissions set for your user.

---

### Post by akakingess on 2010-07-13
The best long-term suggestions that you have gotten is to mount it permanently via fstab, [here]("https://help.ubuntu.com/community/Fstab") is the link for the Ubuntu help file for fstab in case you need to read on how exactly to do it, but that is how I mount all of my partitons that I want to be available each time I log in. If you have any other questions please let us know.

---

