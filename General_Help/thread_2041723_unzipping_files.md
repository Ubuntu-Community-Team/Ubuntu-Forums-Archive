---
title: "unzipping files"
date: 2012-08-13
forum: General Help
---

### Post by DoctorVell on 2012-08-13
Hi there,

I recently got some ROM images that are in .zip format for the M.E.S.S. and I am trying to get them to work so I can  play some old school games (which I have also the ROM images for).  I am trying to get the program to work.  It is giving me an error when I try to uncompress the .zip files, here's the error.  I get this when I do:

unzip 3do.zip
OR
when I go into my Nautius and I right click it and it comes up in the context menu Extract Here.

(NOTE: Using Ubuntu 12.04 with gnome desktop)

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Error: /home/<username>/mess/roms/3do.zip: Can not open file as archive

Errors: 1

Thanks :)

Also if anyone is successful in the MESS.INI files in making it work too, as it says it can not find my ROM images too.

---

### Post by ads52 on 2012-08-13
Are any of these zip files small enough to post to these Forums? It would be nice to test one. Looks like you can post up to 976.6kb for zip files...

---

### Post by Kalanac on 2012-08-13
Double check the file permissions of the zip file and the folder you're extracting to.  You can make sure you're the owner of the file with:

```
chown username:username file.zip
```

That will transfer ownership to the specified username.  Also set the file permissions to a usable default:

```
chmod 644 file.zip
```
(Owner: Read/Write, Group: Read, Other: Read)

Do the same for the folder you plan to extract to.  If all that is done and it still doesn't work then, at a guess, the zip file is corrupted some how, or maybe encrypted/password protected.

---

### Post by codemaniac on 2012-08-13
Need to ensure the integrity of the copied/downloaded zip file .There might be chances of the zip file getting corrupted .
You can use md5 to verify the correctness of the file you have downloaded/copied.

---

### Post by oldos2er on 2012-08-13
Try ```
unzip -t 3do.zip
``` If it shows errors, try ```
zip -FF 3do.zip
``` No guarantees it'll work though.

---

### Post by DoctorVell on 2012-08-13
Didn't work, I might just try and find new roms & try again.

---

### Post by marlow59 on 2012-08-13
then your file is corrupted. please mark the thread as solved.

---

