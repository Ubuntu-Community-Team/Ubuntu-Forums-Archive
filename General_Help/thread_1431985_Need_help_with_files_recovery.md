---
title: "Need help with files recovery"
date: 2010-03-17
forum: General Help
---

### Post by Gintautas on 2010-03-17
I decided to delete windows, and leave ubuntu as the only OS for my computer. So i copied files i needed to other partition that i made as "home" folder. But then my ubuntu bugged, and i couldnt see no files i moved from windows. I reinstalled ubuntu, deleted windows, now i still cannot see files. From hard disk used space i see that these files are still in my hard drive, but i can neither see them or do something with them. How or with what program i can recover these files for normal usage? Thank you.

---

### Post by bobcollard on 2010-03-17
> **Gintautas said:**
> I decided to delete windows, and leave ubuntu as the only OS for my computer. So i copied files i needed to other partition that i made as "home" folder. But then my ubuntu bugged, and i couldnt see no files i moved from windows. I reinstalled ubuntu, deleted windows, now i still cannot see files. From hard disk used space i see that these files are still in my hard drive, but i can neither see them or do something with them. How or with what program i can recover these files for normal usage? Thank you.
If the partition is formated for NTFS then you need to be able to read and write to NTFS from Linux.  Try this link:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Gintautas on 2010-03-17
No, I've formatted the partition as ext4. I used this guide: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by bobcollard on 2010-03-17
> **Gintautas said:**
> No, I've formatted the partition as ext4. I used this guide: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)
Then you should be able to see it in your File Manager on the left side, top portion.

---

### Post by Gintautas on 2010-03-18
But i still dont see any of these old files.

---

### Post by bobcollard on 2010-03-18
> **Gintautas said:**
> But i still dont see any of these old files.
Did you click on the name of the partition in the upper left?  That will highlight and open it for file viewing.

---

### Post by Gintautas on 2010-03-19
Of course i did, as i reinstalled ubuntu i think these files remained somehow "user protected" viewable just for that user or something, its more serious thing then you think :>

---

### Post by bobcollard on 2010-03-19
> **Gintautas said:**
> Of course i did, as i reinstalled ubuntu i think these files remained somehow "user protected" viewable just for that user or something, its more serious thing then you think :>
If you have changed your user name, it is a matter of permissions.  Open Users and Groups and create a User with the same name as you had before.  That may give you the edge you need to get into those files and make then visible to All Users.  I have no idea how you set up your files.  I'm just trying to help out.  Not a Tech, just another user like yourself.

---

### Post by Gintautas on 2010-03-19
Well user has same name and even same password as before still not working :>

---

### Post by bobcollard on 2010-03-19
> **Gintautas said:**
> Well user has same name and even same password as before still not working :>
Can you check permissions on the partition or the main directory/folder?  I don't know the way your file system was set up.  Sometimes you can make all subdirectories follow the same rules.

---

### Post by pandion on 2010-03-29
Just to confirm, when you reinstalled Ubuntu did you let it format your partition again? If you didn't format it and are certain the files are actually there, try running nautilus (or whatever file browser you use) as root. You can do this by pressing ALT+F2 keys at the same time. This will open a Run Command box. Enter "gksu nautilus" as the command. It will prompt for your password and open nautilus. Then try browsing to the folder and see if you can see/access the files.

---

