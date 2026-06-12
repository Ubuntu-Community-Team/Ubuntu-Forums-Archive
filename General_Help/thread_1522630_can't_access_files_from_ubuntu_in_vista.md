---
title: "can't access files from ubuntu in vista"
date: 2010-07-02
forum: General Help
---

### Post by arsenal1 on 2010-07-02
I have an external hard drive with all sort of stuff in there ..the thing is ,i connected my external hdd to my laptop while using ubuntu ,and i renamed some folders ,for example i had the folder EVOLVE and I changed the name to EVOLVE *** ,and i did that to some other folders on my external hdd while in ubuntu ...  the thing is that now i don't have ubuntu instaled anymore ,i have vista ,and when I connect the external hdd i can't access the folder EVOLVE *** and the other ones that I renamed in ubuntu ... can't access it,can't delete it ,can't access proprieties under right click ,can't rename ,can't do anything...when i right click among the other things that apear is @shell32.dll,-8506 


anyone can help ? I really want to be able to access my files

---

### Post by cariboo on 2010-07-02
Why not boot from the Live CD and rename the directories/files to something Windows can read.

---

### Post by WorMzy on 2010-07-02
Linux will let you name file and folders anything, so long as it doesn't have a "/" in it, Windows doesn't allow file/folder names which have a variety of characters in them, such as " * : < > ? \ / |, if you put any of these characters into a filename on a Windows partition, then Windows will not be happy. As Cariboo suggested, boot a Live CD and rename the folder. Or run chkdsk, which should detect the "illegal" filenames and rename them. (It may also move them to a folder in the root of the partition called "000.found", or something similar)

---

### Post by arsenal1 on 2010-07-03
thanks guys ,I booted from the ubuntu live cd ,I renamed the files ,deleted the * characters, so vista is happy now...thanks a lot

---

