---
title: "Files &amp; Memory Issues"
date: 2010-10-24
forum: General Help
---

### Post by Mohsin Saeed on 2010-10-24
What is the Relation of Files with memory when we remove some files using rm commands, does they really remove?
and what's the size of the file; yes it represent on type but of all types?
Best Regards

---

### Post by Mohsin Saeed on 2010-10-24
What is the Relation of Files with memory when we remove some files using rm commands, does they really remove?
and what's the size of the file; yes it represent on type but of all types?
Best Regards

---

### Post by sikander3786 on 2010-10-24
> **Mohsin Saeed said:**
> What is the Relation of Files with memory when we remove some files using rm commands, does they really remove?
and what's the size of the file; yes it represent on type but of all types?
Best Regards
rm command is intended for deleting files and directories.

Do you mean that you want to remove installed programs?

---

### Post by matt_symes on 2010-10-24
Hi 

rm removes the file. It leaves the file on the drive but removes references to it, so you can write on top of it.

i don't understand this

> what's the size of the file; yes it represent on type but of all types?

Kind regards

---

### Post by Mohsin Saeed on 2010-10-24
No basically I want to know, when we delete some file(directory etc) then what's happening at the backend from the point of view of memory like 
1) how much meory is released & on what basis?
2) is it released temporary or something like that?

---

### Post by Davor Posavec on 2010-10-24
When the system remove a program. 
 The program is not completely deleted, it's back upped

---

### Post by Mohsin Saeed on 2010-10-24
means files are just unrefrenced & not acutally removed?
 
Sorry; I want to ask that what are the sizes of files
1) empty text file
2) directory 
3) etc

---

### Post by cavh on 2010-10-24
I think you're confused between memory (RAM, which is volatile and the contents of which don't persist between reboots) and disk space (files written to disk do persist between reboots).

The following command

```
man rm
```

tells you that 'if  you use rm to remove a file, it is usually possible to recover the contents of that file.  If you want more assurance that the contents are truly unrecoverable, consider using shred.'

To see how full your disk(s) are:

```
df -h
```

in a terminal

---

### Post by Mohsin Saeed on 2010-10-24
cavh:
 
yes i'm a bit confused on it, but confusion starts from the size of the file
like initially when any file is created what is the size of the file?

---

### Post by howefield on 2010-10-24
Threads merged,

One issue - one thread please.

---

### Post by Mohsin Saeed on 2010-10-24
Davor Posavec:
 
ok, but initially what's the size of file?
& how can I recover from backup or say I have some private files that I dont want to be even
backuped then what to do?

---

### Post by cavh on 2010-10-24
If an empty file is created, the size is zero. You create an empty file with the 

```
touch
```

command.

with all respect, I think you're getting too hung up on what is an esoteric matter for a Ubuntu newbie.:)

---

### Post by Mohsin Saeed on 2010-10-24
howefield:
 
sorry, I'm New here, will try to be more precise :)

---

### Post by howefield on 2010-10-24
> **Mohsin Saeed said:**
> howefield:
 
sorry, I'm New here, will try to be more precise :)

No problem, and by the way, welcome to the forums :-)

---

### Post by matt_symes on 2010-10-24
Hi

yes files lose their references but they are still on the disk . This is how software recovery programs work, they are still locatable. 

As for the size of empty files and directories, it might  be worth looking through the source code. I never have but you have piqued my curiosity (thanks). What file system are you running? ext 2, 3, 4 etc

Kind regards

---

### Post by Mohsin Saeed on 2010-10-24
howefield: 
Thanks a lot, I'm so so so impressed that how people help here 
& how much they are passionate & devoted!!!!!
 
 
Thanks to all,

---

### Post by Mohsin Saeed on 2010-10-24
matt_symes:
I'm running ext 4 & from where to get the source code :)

---

### Post by Mohsin Saeed on 2010-10-24
cavh: 
:) 
but how the size could be zero???

---

### Post by Mohsin Saeed on 2010-10-24
say if the file just created is of size 0 then where is the metadata of file is stored other than FILE table in Linux

---

### Post by Davor Posavec on 2010-10-24
When you removed only what remains is the Back Up of the program.

---

### Post by Mohsin Saeed on 2010-10-24
Davor Posavec:
 
where this backup resides? & how to off this backup?

---

### Post by Davor Posavec on 2010-10-24
One way to remove the back up is a software called "Tune Up Utilities".
download : [http://www.tune-up.com/download/](http://www.tune-up.com/download/)
You don't need to put your real e-mail.

---

### Post by Mohsin Saeed on 2010-10-24
thanks, but how to recover backup?
 
& still my issue of the file size what's the file size when it's just created?

---

### Post by howefield on 2010-10-24
> **Davor Posavec said:**
> One way to remove the back up is a software called "Tune Up Utilities".
download : [http://www.tune-up.com/download/](http://www.tune-up.com/download/)
You don't need to put your real e-mail.

Hello and welcome to the forum.

Are you aware that this is a forum for Ubuntu users and issues.

---

### Post by Davor Posavec on 2010-10-24
sure, I' am a Ubuntu User.  i only try to help those people. :(

---

### Post by Mohsin Saeed on 2010-10-24
howefiled: 
kindly tell in this case as **Davor Posavec **have assisted me what's the solution, like how to communicate such links etc?

---

### Post by howefield on 2010-10-24
> **Davor Posavec said:**
> sure, I' am a Ubuntu User.  i only try to help those people. :(

And very admirable too. :)

There are few circumstances to justify promoting a Windows application to fix an Ubuntu issue. This probably isn't one of them.

---

### Post by Davor Posavec on 2010-10-24
> **howefield said:**
> And very admirable too. :)

There are few circumstances to justify promoting a Windows application to fix an Ubuntu issue. This probably isn't one of them.



OK. Never Mind. :(

---

### Post by Davor Posavec on 2010-10-24
I hate when Admins are PWNING me!!!  :lolflag:

---

### Post by Mohsin Saeed on 2010-10-24
guys now I'm hoping for some great answers from great users of linux-ubuntu!

---

### Post by Mohsin Saeed on 2010-10-28
hey guys need help, plz

---

