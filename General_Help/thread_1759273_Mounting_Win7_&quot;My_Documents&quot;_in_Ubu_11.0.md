---
title: "Mounting Win7 &quot;My Documents&quot; in Ubu 11.05"
date: 2011-05-15
forum: General Help
---

### Post by JohnnyB98604 on 2011-05-15
I want to mount my windows drive so I can get to My Documents.  When I navigate to the Home folder, I don't see it in the list of "Places".

Any suggestions?

Resolution:
> **Morbius1 said:**
> Look at > File System > /host when you go into your home folder.

---

### Post by belltown on 2011-05-15
> **JohnnyB98604 said:**
> I want to mount my windows drive so I can get to My Documents.  When I navigate to the Home folder, I don't see it in the list of "Places".

Any suggestions?

Under Places, do you see something like "xxx GB Filesystem"? If so, click on it and it should open your Windows partition. Your Windows My Documents should be under Users>username>Documents. Then under Bookmarks, click Add Bookmark, which will add a shortcut to your Places for your Windows documents.

---

### Post by m1tchy24 on 2011-05-15
i do this all the time but with win xp go to computer and go on harddisk that windows is installed on go to users and select your documents. then make a shortcut in ur ubuntu docs and put the link as /(harddisk)/users/(Tom)/My documents. it will give you quick access. you dont have to worry about admin rights cos ntfs partitions arent encrypted in ubuntu so you can access anyones docs, windows is less secure than ubuntu by far.

---

### Post by JohnnyB98604 on 2011-05-15
> **belltown said:**
> Under Places, do you see something like "xxx GB Filesystem"? If so, click on it and it should open your Windows partition. Your Windows My Documents should be under Users>username>Documents. Then under Bookmarks, click Add Bookmark, which will add a shortcut to your Places for your Windows documents.

I do have an item like that but it's not windows.  It's an SD card that I have stuck in the reader.  When I remove it, the item is dropped from "Places".

---

### Post by JohnnyB98604 on 2011-05-15
> **m1tchy24 said:**
> i do this all the time but with win xp go to computer and go on harddisk that windows is installed on go to users and select your documents. then make a shortcut in ur ubuntu docs and put the link as /(harddisk)/users/(Tom)/My documents. it will give you quick access. you dont have to worry about admin rights cos ntfs partitions arent encrypted in ubuntu so you can access anyones docs, windows is less secure than ubuntu by far.

Thanks, I'm going to try this suggestion now.

---

### Post by JohnnyB98604 on 2011-05-15
> **JohnnyB98604 said:**
> Thanks, I'm going to try this suggestion now.

To be clear, I'm going to log in to Ubuntu and add shortcut to this destination?

(C:\Users\john borgen\Documents)

I ask because I don't see the Ubuntu folder in Windows 7 either.  This could be an important fact I left out, this is a WUBI installation/upgrade from 10.04

---

### Post by Morbius1 on 2011-05-15
Look at > File System > /host when you go into your home folder.

---

### Post by JohnnyB98604 on 2011-05-15
> **Morbius1 said:**
> Look at > File System > /host when you go into your home folder.

Excellent!  That gets me what I'm looking for.

Thank you.

---

