---
title: "Opening PDF documents"
date: 2011-08-12
forum: General Help
---

### Post by aoniumo on 2011-08-12
I download PDF documents from online into my computer like credit card statements, bank statements, mutual fund information, etf information, etc.  I am using document viewer to open them.  When I have these documents on my desktop I can open these documents.  When I move them to a different drive on my computer (also ext4 format), Document Viewer can no longer open them.  It gives me this error.  Unable to open document Error opening file: Permission denied  Could anyone help with this?

---

### Post by hyfanious on 2011-08-13
:))
hi dude
permission errors are happened due to simply PERMSISIONS :))
in fact u copy them in some where and for some other reasons their permissions change and u no longer able to see them
just do this:
right-click on that file -> select properties -> permission tap
and set the options in appropriate way

or

in terminal :

sudo chmod o+w /path/of/ur/file/file.pdf

---

### Post by hyfanious on 2011-08-13
or use this :
```
sudo chmod 777 /path/of/ur/file/fie.pdf
```


but be careful in using this one
U can find many article about permission in the web
U need to know about that completely, since u using linux
PLZ check this out:
[HTML]https://help.ubuntu.com/community/FilePermissions[/HTML]

---

### Post by aoniumo on 2011-08-13
> **hyfanious said:**
> :))
hi dude
permission errors are happened due to simply PERMSISIONS :))
in fact u copy them in some where and for some other reasons their permissions change and u no longer able to see them
just do this:
right-click on that file -> select properties -> permission tap
and set the options in appropriate way

or

in terminal :

sudo chmod o+w /path/of/ur/file/file.pdf


I changed permissions.  Please see screenshot, but still unable to open.

---

### Post by mystika1 on 2011-08-13
Hi,
I have had this problem also. I switched to Okular and no longer have trouble viewing any PDF documents.

HTH,

Penny

---

### Post by hyfanious on 2011-08-13
so I guess its permission error must be related to ur folder which contains ur file
can u check that too?
be aware of using that codes to ur entire folder
if that partition is not a systemic partition u can use this code:
```
sudo chmod -R 777
```
this "-R" is stands for meaning of "recursively" that means change ur folder and subfolders and contents permissions
so be aware of using that
If u see that article u can find everything u need
but if that is a bit confusing just asking here ;)

---

### Post by aoniumo on 2011-08-13
> **hyfanious said:**
> so I guess its permission error must be related to ur folder which contains ur file
can u check that too?
be aware of using that codes to ur entire folder
if that partition is not a systemic partition u can use this code:
```
sudo chmod -R 777
```this "-R" is stands for meaning of "recursively" that means change ur folder and subfolders and contents permissions
so be aware of using that
If u see that article u can find everything u need
but if that is a bit confusing just asking here ;)

I changed the permissions of the drive and folder to read and write and checked allow executing program, but still nothing.  I tried using Gimp to open it, and it opened but Gimp is not ideal for viewing multi-page PDFs.  I'll try to find a program that can open these documents.

---

### Post by hyfanious on 2011-08-13
wow
I guess I had same problem and I solved it just by rearranging permissions
but if u think your problem is related to ur viewer u have plenty of ways :)
u can run viewer in terminal with sudo prefix
or using other viewer like Okular - xournal (mine favorite) - ... (just google it)

---

