---
title: "Ubuntu is driving me crazy - file permissions? help"
date: 2006-04-09
forum: General Help
---

### Post by engineering.concepts on 2006-04-09
I am working on a new website, (zip file I purchased) and I just spent the last 4 hours trying to get the index.html to work online. My browser would always give me a ERROR 403. I could view it fine with NVU and with Firefox or Opera off of my hard drive, but the second I uploaded it (using gftp) it would be toast.
I also tried with images and nothing would work.
I finally transferred the zip file to my wife's WinXp computer and uploaded the files, and everything works perfectly!!!!

I have been singing the praises of Ubuntu for the last 30 days, and I almost smashed my laptop this morning.

I am hoping that I am stupid and did not set a file permission correctly? ](*,)

I tried to change the permissions of the jpg's to read/write/execute for all users and tried to upload again, but I get the same error.

I would prefer to edit my webpages on Ubuntu and ftp them myself , but I don't think it's an option because :-# I hate to admit this - but WinXp just works. (in this instance)

---

### Post by xXx 0wn3d xXx on 2006-04-09
[QUOTE=engineering.concepts]I am working on a new website, (zip file I purchased) and I just spent the last 4 hours trying to get the index.html to work online. My browser would always give me a ERROR 403. I could view it fine with NVU and with Firefox or Opera off of my hard drive, but the second I uploaded it (using gftp) it would be toast.
I also tried with images and nothing would work.
I finally transferred the zip file to my wife's WinXp computer and uploaded the files, and everything works perfectly!!!!

I have been singing the praises of Ubuntu for the last 30 days, and I almost smashed my laptop this morning.

I am hoping that I am stupid and did not set a file permission correctly? ](*,)

I tried to change the permissions of the jpg's to read/write/execute for all users and tried to upload again, but I get the same error.

I would prefer to edit my webpages on Ubuntu and ftp them myself , but I don't think it's an option because :-# I hate to admit this - but WinXp just works. (in this instance)[/QUOTE]

Did you do an expert install ?

---

### Post by Stormbringer on 2006-04-09
Uploading with gFTP is kind of tricky ...

The files you upload to your FTP by gFTP will keep the permissions they have on your local hard drive - i.e. 660 which is rw- rw- --- (user group others). In Windows it works because the permissions get dropped.

Once you uploaded the files on your FTP server simply check their permission (Select the files in the external file list, do a right-click, and select "Chmod...").

Set them to something like 664 which is rw- rw- r-- (user group others) and try again.

[EDIT]
Alternatively you can change gFTP's behaviour so that you mustn't bother about the permissions:

Lauch gFTP.
Menu "FTP" -> "Options" -> Tab "General"
UNCHECK "Preserve File Permissions" -> Click "Apply" and "OK"
[/EDIT]

Cheers,
Storm.

---

### Post by kingmonkey on 2006-04-09
this is probably binary/ascii ftp transfer misconfiguration.

---

### Post by engineering.concepts on 2006-04-09
[QUOTE=Stormbringer]Uploading with gFTP is kind of tricky ...


[EDIT]
Alternatively you can change gFTP's behaviour so that you mustn't bother about the permissions:

Lauch gFTP.
Menu "FTP" -> "Options" -> Tab "General"
UNCHECK "Preserve File Permissions" -> Click "Apply" and "OK"
[/EDIT]

[/QUOTE]

WHOOOOO HOOOOOOOOO!!!!!!:D 
That did it - Once I UNCHECK "Preserve File Permissions" everything worked great!!!!!!
No More WinXP for MEEEEEEEE!!!!!
Now I can get back in Love with Ubuntu!!!!!!!

---

### Post by Stormbringer on 2006-04-09
Well, well, one more happy user ... glad you got your problem sorted out.

Happy Ubuntuing,
Storm.

---

