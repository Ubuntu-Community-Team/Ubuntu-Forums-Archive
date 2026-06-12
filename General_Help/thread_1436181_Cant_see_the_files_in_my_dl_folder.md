---
title: "Cant see the files in my dl folder"
date: 2010-03-22
forum: General Help
---

### Post by Theomi on 2010-03-22
I have a wierd problem that i need help with, i have ubuntu karmic and win7 installed side by side and so i got a shared disk for all my stuff...
This device is mounted as /media/storage in ubuntu and in there i have a download folder which until recently worked...

Now when i download to /media/storage/download the download finishes but when i look in download (browsing folders) the new files are not there..
The old files which also where there before is still there tho... 
Strange thing is that if i do a ls /media/storage/download in bash it's all there, both old and new files... 

Im scratching my head here... :confused:

---

### Post by N92 on 2010-03-22
Have you tried _**ctrl+h**_ when you open the folder?

---

### Post by Theomi on 2010-03-23
Ye that was the first i tried...
I discovered yesterday after posting that doing a ls in the dir i get an input/output error on some of the files....
And i cant delete the folder either

---

### Post by geirha on 2010-03-23
I'd try a filesystem check. For NTFS, you'll have to boot into windows to check it though.

---

### Post by Theomi on 2010-03-23
[LEFT]Hmm didnt think of that :-\":-\":-\" i'll give it a try thx
[/LEFT]

---

