---
title: "Ubuntu won't show the drive on which it is installed! pls help!"
date: 2010-09-08
forum: General Help
---

### Post by Evil Eye on 2010-09-08
okay so i installed Ubuntu using wubi on my Windows 7 laptop

i installed Ubuntu on D: drive of my laptop
now when i run Ubuntu, it shows only C: drive and not the D: drive on which i have installed it

pls help

thanks in advance :)

---

### Post by Joe of loath on 2010-09-08
Ubuntu won't show the drive it's installed on, however you can access the whole filesystem (including mounted drives), but clicking on the 'filesystem' icon in the 'computer' window.

---

### Post by Evil Eye on 2010-09-08
@joe how do i access files and folders of my D: drive?

i am unable to see them in the file system

---

### Post by Joe of loath on 2010-09-08
The folders in the file system are 90% on the root hard disk, the one you installed on. What are you looking for?

---

### Post by Evil Eye on 2010-09-08
@joe my movie, music etc files and folders are on D: drive, so searching for them, couldnt find them in file system..

---

### Post by Joe of loath on 2010-09-08
If you installed it on the drive with all your data on, you had to format it. Unfortunately, you've now lost all your data.

---

### Post by Evil Eye on 2010-09-08
> **Joe of loath said:**
> If you installed it on the drive with all your data on, you had to format it. Unfortunately, you've now lost all your data.

nah man, i have done the installation using WUBI on Windows 7

all the data is still on D: drive man, the files and folders are accessible on Windows 7 but can't see them on Ubuntu

---

### Post by coffeecat on 2010-09-08
> **Evil Eye said:**
> all the data is still on D: drive man, the files and folders are accessible on Windows 7 but can't see them on Ubuntu

Here you go:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> 
**How do I access the Windows drives?**

 The  Windows partition where you installed Wubi is available as /host within  Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable mediaHave a look in the Places menu. It won't be called the D: drive, because C:, D: etc is Microsoft terminology. You'll recognise it in the Places menu, either by the partition label or the size of the partition. If it's not labelled, the next time you are in Windows, go to (My) Computer, right-click on the D: drive and choose rename - say 'Data', 'Myfiles', whatever you want. Then this name will appear in the Places menu next time you are in Ubuntu

---

### Post by Joe of loath on 2010-09-08
Ohh, duh. Ignore everything I said then...

(I'm going to blame it on the meds.)

---

### Post by Evil Eye on 2010-09-09
@coffecat thanks mate, i found it in host of filesystem
@joe thanks for the help too

---

### Post by CAPLinux on 2010-09-10
@CoffeeCat Thanks for helping me too!!

---

