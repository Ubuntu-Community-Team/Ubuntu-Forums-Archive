---
title: "protection"
date: 2011-08-13
forum: General Help
---

### Post by ajits on 2011-08-13
How can I protect a file or folder from unauthorized delete.:)

---

### Post by ~!geek!~ on 2011-08-13
Learn Permissions system in linux. It will help you more than what you asked for:
Refer this link:
[http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php)

---

### Post by raja.genupula on 2011-08-13
hey give the permission only for reading ```
chmod 700 filename
```
so no one modify it, only the user

---

### Post by ajits on 2011-08-13
> **raja.genupula said:**
> hey give the permission only for reading ```
chmod 700 filename
```so no one modify it, only the user
  how it use

---

### Post by haqking on 2011-08-13
what do you mean how it use ?

you mean how do you use it ?

type it in to terminal as shown and replace filename with the file you dont want deleted

---

### Post by The Cog on 2011-08-13
> **raja.genupula said:**
> hey give the permission only for reading ```
chmod 700 filename
```
so no one modify it, only the user
Unfortunately, that doesn't prevent files from being deleted, although it prevents non-owners from viewing or editing the file. This is because you only need write access to the containing directory in order to delete a file. 

All I can think of is to place the file in a folder and then remove write access to the folder. Example:
```
chmod -w foldername/filename
chmod -w foldername
```
These commands would be used on the command line. You can do the same thing in the GUI by right-clicking the file/folder and setting permissions to remove write access.

---

### Post by Duncan Williams on 2011-08-13
install truecrypt
make a 50mb encrypted partition
mount this and save your files in the directory.
dismount at any time (1 click)
you require 2 passwords to remount.

Your 50mb safe for your private files.

---

### Post by Soul-Sing on 2011-08-13
> **ajits said:**
> How can I protect a file or folder from unauthorized delete.:)

zip it with pass protection, without a pass there is no delete afaik.

---

### Post by ajits on 2011-08-14
> **leoquant said:**
> zip it with pass protection, without a pass there is no delete afaik.
may I get step by step information to do it?

---

### Post by 3rdalbum on 2011-08-15
I think this is what you're really after:

[http://www.cyberciti.biz/faq/how-to-make-a-file-unchangeable-unalterable-so-that-no-one-can-modify-it/]("http://www.cyberciti.biz/faq/how-to-make-a-file-unchangeable-unalterable-so-that-no-one-can-modify-it/")

Also prevents deletion.

---

### Post by Soul-Sing on 2011-08-15
> **ajits said:**
> may I get step by step information to do it?

rightmousebutton on the file: (in dutch) comprimeren (compress in English?): choose passwd protection.

---

### Post by ajits on 2011-08-15
> **haqking said:**
> what do you mean how it use ?

you mean how do you use it ?

type it in to terminal as shown and replace filename with the file you dont want deleted
sorry sir ,I can't do it .may I get step by step procedure.

---

### Post by The Cog on 2011-08-15
> **3rdalbum said:**
> I think this is what you're really after:

[http://www.cyberciti.biz/faq/how-to-make-a-file-unchangeable-unalterable-so-that-no-one-can-modify-it/]("http://www.cyberciti.biz/faq/how-to-make-a-file-unchangeable-unalterable-so-that-no-one-can-modify-it/")

Also prevents deletion.

Thank you, 3rdalbum. I had a feeling that access lists could do it, but I'm not familiar with them. That does look exactly right.

---

### Post by Primefalcon on 2011-08-15
> **The Cog said:**
> Thank you, 3rdalbum. I had a feeling that access lists could do it, but I'm not familiar with them. That does look exactly right.
I do the same thing when I absolutely do not what files modifed, for example on my netbook I dont want a list of recent docs...

so I basically wipe the file, create a blank one and chattr it, so it cannot be modified from an empty doc

---

### Post by The Cog on 2011-08-18
> **Primefalcon said:**
> I do the same thing when I absolutely do not what files modifed, for example on my netbook I dont want a list of recent docs...

so I basically wipe the file, create a blank one and chattr it, so it cannot be modified from an empty doc
That's one for the memory bank.
 I also noticed chattr +a which makes a file impossible to delete or overwrite, but possible to append - ideal for log files.

---

### Post by cryptotheslow on 2011-08-19
Just for my own sanity - wouldn't setting the sticky bit on the containing directory do the job for the OP?

i.e. chmod 1700 on the directory.

As far as I understand it that would stop other users deleting the files contained within (presuming the OP owns the directory and files). Wouldn't stop a sudo'er I don't suppose.

Just asking as I'm not entirely sure my understanding of it is correct :popcorn:


Edit - after some further reading it seems for this to be an effective solution one would have to create two directories, one inside the other and sticky bit them both otherwise an rm -rf of the single stickied directory would be possible taking the files with it. I think I need to experiment and see if my theory is correct :)

---

