---
title: "An Ubuntu newbie in need of some serious help."
date: 2009-10-12
forum: General Help
---

### Post by Rogercorman on 2009-10-12
Hi! I love Ubuntu, and I think it's great, but it would be even better if I could get this one thing to work:

When I go to record something with the built in sound recorder, or when I try to save a document, etc. it tells me that I don't have enough hard disk space to preform the task. I emptied the trash and ran a command in terminal which escapes me at the moment, (but it's the equivalent of a disk cleanup). Still, I can't record anything! Please help, I wanted to try and get some stuff done tonight.

NOTE: I installed Ubuntu with Wubi at the lowest number of gigs possible. Could this have something to do with it?

Much appreciated!

---

### Post by Giblet5 on 2009-10-12
Your apps are telling you that you have insufficient disk space and you still have questions?

A [1TB hard disk]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4306125&CatId=2459") is $80. Times are tough, I know, but c'mon!

---

### Post by lrcaballero on 2009-10-12
Hi there,

Try using SUN Virtual Box and/or Virtual Machine from MS these 2 programs are very easy and friendly user with MS and Linux, I have heard many problems with people using the program you are using witch is Woobie (Correct??) to answer your question you probably gave very little space to Linux, make sure you use at least 1024 MB of Memory and 16 GB of Ram. Good Luck!!!


Luis  

:guitar:

---

### Post by drs305 on 2009-10-12
> **Rogercorman said:**
> 
NOTE: I installed Ubuntu with Wubi at the lowest number of gigs possible. Could this have something to do with it?

Yes, it has everything to do with it. When you elected to install wubi with a minimum size, a file was created in Windows for wubi. The file size can't change, so more than likely you don't have any 'extra' room in your wubi install to save much data. 

Your options are to store the data to another partition outside of wubi, reinstall wubi in Windows with a larger file size, or do a regular wubi install on its own partition.

You can also move your /home partition elsewhere using LVPM, but this starts getting more complicated than you want.

Take a look at the wubi wiki page:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")

---

### Post by Rogercorman on 2009-10-12
Thanks everyone! I probably should have mentioned that I can save things, but it's only those two apps. Anyway, I'll reinstall Ubuntu with Wubi with more alloted disk space. 

Like I said, just got into Linux, have no idea how most of it works as of yet.

---

### Post by stinger30au on 2009-10-12
> **Rogercorman said:**
> Thanks everyone! I probably should have mentioned that I can save things, but it's only those two apps. Anyway, I'll reinstall Ubuntu with Wubi with more alloted disk space. 

Like I said, just got into Linux, have no idea how most of it works as of yet.

its cool dude


we all got to learn somehow

---

### Post by 3rdalbum on 2009-10-12
> **Rogercorman said:**
> Thanks everyone! I probably should have mentioned that I can save things, but it's only those two apps. Anyway, I'll reinstall Ubuntu with Wubi with more alloted disk space. 

Like I said, just got into Linux, have no idea how most of it works as of yet.

Wubi installs top out at 30 gigabytes (you can't allocate any more than that). You might want to try out a real dual-boot install; just make sure you read my signature (about allocating space for Ubuntu) before doing the "resize partition" bit.

---

