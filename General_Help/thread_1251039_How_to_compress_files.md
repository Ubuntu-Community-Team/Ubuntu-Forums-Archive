---
title: "How to compress files?"
date: 2009-08-27
forum: General Help
---

### Post by gaastra on 2009-08-27
if you right click the folder ther eis compress folder option, but I would just like to compress it like in winrar as store.

see i have like 50 Gigs of images ^ if I move them around, it takes forever, it also takes forever to zip them, but if you winrar store them it goes fast. 

how can I do it in ubuntu ?

[B]EDIT:
read last post, it says use tar compression or copy 25GB at once if you go more, ubuntu slows down to like 5 hours etc...[/B]

---

### Post by pedro_orange on 2009-08-27
> **gaastra said:**
> if you right click the folder ther eis compress folder option, but I would just like to compress it like in winrar as store.

see i have like 50 Gigs of images ^ if I move them around, it takes forever, it also takes forever to zip them, but if you winrar store them it goes fast. 

how can I do it in ubuntu ?

Go to the folder you want to compress. Right click it, Archive. 

This creates a zipped file (Denoted .gz)

---

### Post by gaastra on 2009-08-27
> **pedro_orange said:**
> Go to the folder you want to compress. Right click it, Archive. 

This creates a zipped file (Denoted .gz)

Yes but its slow as hell, I dont want to compress it, just put all files into 1 file container, without compressing data, so I wont need to wait 5 hours to transfer the data from 1 HDD to another.

Imagine 50 Gigs of image transfer...it takes forever

---

### Post by muteXe on 2009-08-27
could you tar it?  This wont compress it, and it'll put it all in one file.

---

### Post by P4man on 2009-08-27
If you want to use rar (winrar is just a shell) then type this in a terminal:

```
sudo apt-get install rar
```

Then you can right click a folder or file, create archive, and select "rar" as type.

im curious though what type of images they are? If its a compressed format like jpg or png then you can't compress them any furter...

---

### Post by kjohri on 2009-08-27
GO to the top level directory, say

cd 

tar -cvjf <compressed archive> *

It will make a compressed archive of all files recursively in current directory and its sub-directories.

To retrieve files,

tar -xvjf <compressed archive>

---

### Post by muteXe on 2009-08-27
But wont that bzip?  Which takes more time than a gzip (tar -czvf ....).

---

### Post by gaastra on 2009-08-27
they are little disgusting *.jpg files. (50KB - 1MB)


Actualy I just found something interesting, I tried copying 25 GB folder and it shows me 28 minutes instead 6 hours.

Ill try to copy little by little, 25 Gig chunks, maybe it will go faster and I wont have to zip them

Another note, I copied 3 GB file and it took 2 minutes. and if I calculate now. I get this:

to copy 3 GB -> 2 minutes
to copy 25 GB -> 28 minutes
to copy 50 GB -> 6 hours
split 25 Gigb into 3 GB files and copy -> 17 minutes

---

### Post by 3rdalbum on 2009-08-27
File Roller (Archive Manager on Gnome) can create Rar and Tar archives.

---

### Post by gaastra on 2009-08-27
> **3rdalbum said:**
> File Roller (Archive Manager on Gnome) can create Rar and Tar archives.

I tried already 7 zip thingie for linux, but I did not understand how to use it.

So how I install & use it ?

is my first time installing someting in ubuntu

---

### Post by XCan on 2009-08-27
As said multiple time above. You should try out using .tar only! Right click on the folder -> Create Archive -> Select .tar. If you don't want to compress it, installing bunch of compression softwares does not make sense. Just use .tar.

---

