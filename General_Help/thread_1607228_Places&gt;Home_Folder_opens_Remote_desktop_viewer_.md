---
title: "Places&gt;Home Folder opens Remote desktop viewer (help)"
date: 2010-10-27
forum: General Help
---

### Post by vie et mort on 2010-10-27
I was using remote desktop viewer to do some work on my windows 7 desktop and I had just added the remote desktop viewer launcher to my panel when my laptop unexpectedly shutdown. I restarted and when I clicked the "Home Folder" under "Places" on the top panel it opened Remote Desktop Viewer instead of taking me to "/home/reinhardt". It does this for "Desktop", "Documents", "Music", "Pictures", "Videos" and "Downloads" each time giving me the respected error:

"The following error has occurred: /home/reinhardt: Can't open directory"
and in turn opening Remote Desktop Viewer.

In terminal "gnome-open /home/reinhardt" results in the same process.

If I click the "Computer" link under "Places" that will open and I can navigate to my desired folder from there, But small things like this drive me crazy!

If anyone knows of a possible solution I would love to hear it.

-ubuntu 10.10


Regaurds

Cory

---

### Post by vie et mort on 2010-10-27
Any clues out there?

---

### Post by plucky on 2010-10-27
Open a terminal and ```
nautilus
```

In the window that opens right click on a folder and select **Open with Other Application**.

When the list opens, select **File Browser** which should now associate folders with the File Browser Application.


Good Luck

---

### Post by endotherm on 2010-10-27
if that fails, find your mimeapps.lst in your profile (I think it may be under ~/.gnome2 but hunt around).
then look witin the file for any line that contains the words "rdesktop" or "vinagre", and post them back. the trick is to remove that element from the line, but I can't recall if we need to remove any adjascent info, so jsut post them back for now, if you are feeling faint of heart. if you have not created any custom file type associations anyway, you can just delete the whole mimeapps file if you like.

---

### Post by vie et mort on 2010-10-27
> **plucky said:**
> Open a terminal and ```
nautilus
```

In the window that opens right click on a folder and select **Open with Other Application**.

When the list opens, select **File Browser** which should now associate folders with the File Browser Application.


Good Luck

Perfect. Thank you very much!

---

