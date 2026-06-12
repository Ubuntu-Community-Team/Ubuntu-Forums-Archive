---
title: "Sync thumbdrive and folder"
date: 2010-11-11
forum: General Help
---

### Post by claven123 on 2010-11-11
I am looking for a solution to sync my thumbdrive with a folder in my home directory.  I'm not able to use dropbox or ubuntuone at work anymore :(  so, I need to use a thumbdrive to use files at work.
 
I'm currently storing my files no the thumbdrive, but worry that I might lose my data.
 
So, I would like an application that keeps the thumbdrive and folder in sycn when changes are made to either or when I need to sycn them.
 
Thanks

---

### Post by Crusty Old Fart on 2010-11-11
You might consider: rsync
```

man rsync

```

---

### Post by claven123 on 2010-11-13
I looked at it briefly, but appears complicated.  I will have to look into it a bit further.  I really only want to sync a few files to from one folder to another on a thumb drive.  

Thanks for the info!!

---

### Post by sjhaffner on 2010-11-16
Yea, I have the same question. =) I've looked at the manual for rsync but it looks way over my head. Any help would be greatly appreciated!

---

### Post by pqwoerituytrueiwoq on 2010-11-16
to usb
```
rsync -av --delete /home/$USER/Documents/ /media/someUSB/
```from usb
```
rsync -av --delete /media/someUSB/ /home/$USER/Documents/ 
```
if abc.txt is on you usb and you run command number 1 and abc.txt is not in your documents folder you will loose abc.txt

---

### Post by sjhaffner on 2010-11-16
> **pqwoerituytrueiwoq said:**
> to usb
```
rsync -av --delete /home/$USER/Documents/ /media/someUSB/
```from usb
```
rsync -av --delete /media/someUSB/ /home/$USER/Documents/ 
```
if abc.txt is on you usb and you run command number 1 and abc.txt is not in your documents folder you will loose abc.txt
Thanks! So if I run both commands (one after the other) it will two way sync?

---

### Post by pqwoerituytrueiwoq on 2010-11-16
if you run either one of them tehy will have equal content
command 1 makes basically deletes deletes the content of the usb and puts the content of your documents folder on it just much faster assuming there content is similar
the other one does it the other way

---

### Post by sjhaffner on 2010-11-16
oh, so I would need to only make changes on one or the other and run the right command?

---

### Post by pqwoerituytrueiwoq on 2010-11-17
with the command i posted 
1. Documents -> USB
```
rsync -av --delete /home/$USER/Documents/ /media/someUSB/
```2. USB -> Documents
```
rsync -av --delete /media/someUSB/ /home/$USER/Documents/
```If you just saved MyFile.txt in my documents then run command 2 MyFile.txt will be deleted and everything on your USB will end up in your documents everything that is in documents that is not on your USB will be deleted

You could read the simple help information and edit the command to better suite your needs
```
rsync --help
```i basically copyed the command from a script I use to sync my firefox RAM profile to my HDD profile

---

### Post by sjhaffner on 2010-11-17
OK, thanks a lot! =)

---

