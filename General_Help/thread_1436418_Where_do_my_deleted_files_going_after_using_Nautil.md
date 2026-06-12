---
title: "Where do my deleted files going after using Nautilus?"
date: 2010-03-22
forum: General Help
---

### Post by ClintEastwood1971 on 2010-03-22
Hi All

Newbie here.  

Sorry to ask but can not find a definitive answer to this question.  I use XBMC a lot and recenty i have been trying to download movies i have d/l using SABNZBDPLUS. 

I noticed my 320GB getting low so i tried deleting the files within the folder itself but got this message "Cannot move file to the deeted items folder, do you want to delete permanently?".  Anyway i tried to delete but i guess it would not also the main folder had a lock icon on it.

So i read somewhere you can use nautilus in the terminal and once i navigated to the folder in question i pressed the delete key on my keyboard.  The file is not in my trash can and i dont think is permenantly deleted as my disc space has not been reduced.

Any ideas please?

---

### Post by mikewhatever on 2010-03-23
Usually, when deleted from Nautilus, the files go to .local/share/Trash inside you home folder. But since you say that is empty, try running the following to get get the idea of what's taking the space:

du -sh /* --exclude=/var* --exclude=/proc* --exclude=/etc*

The command will show a summary of folder sizes under /. The most large sized folder is the place to look further. If you need help with that, post the out put of the above command here.

---

