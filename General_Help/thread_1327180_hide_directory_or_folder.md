---
title: "hide directory or folder?"
date: 2009-11-15
forum: General Help
---

### Post by abhilashm86 on 2009-11-15
when i remove read/write permissions from directory,i;m not able block certain files to be opened, 
in windows i remember a software alled magic folder or something, where i gave folder a password, when giving that passwrod again, we can able to open that file, is there anuthing in ubuntu like that? how to do it?
please help, googled no answer!!

---

### Post by Zoot7 on 2009-11-15
You could do this:
```
sudo chown -R $USER:$USER <directory name>
sudo chmod -R 700 <directory name>
```
And put a "." in front of the directory name. That'll make you the owner and change the permissions so that anybody else other than you can't even cd into it.

---

### Post by sisco311 on 2009-11-15
Encrypt it.

[uhelp]/community/EncryptedPrivateDirectory[/uhelp]

---

