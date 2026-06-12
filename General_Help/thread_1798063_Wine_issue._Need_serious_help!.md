---
title: "Wine issue. Need serious help!"
date: 2011-07-05
forum: General Help
---

### Post by xDante on 2011-07-05
Okay, I need serious help as the title suggests, I am on Maverick and every time I install wine from the Ubuntu Software center I can not access my Home, Documents, Downloads, Pictures, Videos, ect. I get a File not Found Error, I have tried installing/reinstalling Wine countless time, and I can only access it when it is off my system. I have looked everywhere but I can find an answer, Please help. :( I attached a screen shot of the error on my desktop.

---

### Post by Bachstelze on 2011-07-05
When exactly does the error occur?

---

### Post by xDante on 2011-07-06
> **Bachstelze said:**
> When exactly does the error occur?

It only occurs if I click on any directory under places, I can use all apps just fine, but when I click on Home folder, Desktop, Documents, Downloads, Pictures, Videos, Music. It gives me the "File Not Found" Error. Any Idea why?

---

### Post by grahammechanical on 2011-07-06
File manager will associate certain file types with certain programs. So, that when you click on that type of file it will be opened by that program.

It is my guess that folders are no longer associated with the file manager. So, that by clicking on Places (which is a folder) the file manager does not run and so does not open that folder. Others have had similar problems. I have also. I fixed it this way:

Right click the desktop and select Create Folder. Right click the new folder and select Open With Other Application. Select File Browser from the list.  By associating this new folder with the File Browser or Manager you will associate all folders with the File Browser.

Regards.

---

### Post by xDante on 2011-07-06
> **grahammechanical said:**
> File manager will associate certain file types with certain programs. So, that when you click on that type of file it will be opened by that program.

It is my guess that folders are no longer associated with the file manager. So, that by clicking on Places (which is a folder) the file manager does not run and so does not open that folder. Others have had similar problems. I have also. I fixed it this way:

Right click the desktop and select Create Folder. Right click the new folder and select Open With Other Application. Select File Browser from the list.  By associating this new folder with the File Browser or Manager you will associate all folders with the File Browser.

Regards.

Thank you so much! It worked! Appreciate it! I'm coming here more often

---

### Post by dino99 on 2011-07-06
> **xDante said:**
> Thank you so much! It worked! Appreciate it! I'm coming here more often

not the good place, wine has its own subforum, so post wine requests there.

---

