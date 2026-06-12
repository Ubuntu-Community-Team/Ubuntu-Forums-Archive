---
title: "Remastersys backups whole partition?"
date: 2009-11-18
forum: General Help
---

### Post by Alm4riC on 2009-11-18
Hi,

I have a (almost) fresh Ubuntu installation and want to Remastersys it to an .iso file, so i can boot it from an external HD. When I start Remastersys (sudo remastersys dist test.iso), the program starts to write a file from 20GB (that's the size of my ext3 partition). This is strange to me because I've done this before and then I got a normal iso file. Not a file from 20GB.

I'm using Ubuntu 9.04

Suggestions? :)

---

### Post by ibuclaw on 2009-11-18
Remastersys is a bit hit and miss.

It's a script, so is not guaranteed to work.

---

### Post by JBAlaska on 2009-11-18
Are you running ```
remastersys backup
``` or ```
remastersys dist
``` Backup will backup your whole partition dist will make a distributable copy.

Or click on the "Remastersys Backup" icon in the System Menu and you can select which option you want to run.

---

### Post by Cheesemill on 2009-11-18
Just to let you know, Remastersys doesn't work properly with 9.10 yet.

EDIT - Yes it does, I hadn't realised the new version was out :)

---

### Post by JBAlaska on 2009-11-18
OP is using 9.04

---

### Post by Alm4riC on 2009-11-19
> **JBAlaska said:**
> Are you running ```
remastersys backup
``` or ```
remastersys dist
``` Backup will backup your whole partition dist will make a distributable copy.

Or click on the "Remastersys Backup" icon in the System Menu and you can select which option you want to run.

I run
```

remastersys dist

```

---

### Post by Alm4riC on 2009-11-19
Anyone? :)

---

### Post by bodhi.zazen on 2009-11-19
remastersys copies your files to /home/remastersys and then compresses them to an iso.

Take care with remastersys , it will change the base (host) system (ie remove users) , at least it has done so to me in the past.

If you are trying to compress 20 Gb of data and files into an iso, good luck, the iso will almost certainly be huge in size as well.

---

### Post by Alm4riC on 2009-11-20
> **bodhi.zazen said:**
> remastersys copies your files to /home/remastersys and then compresses them to an iso.

Take care with remastersys , it will change the base (host) system (ie remove users) , at least it has done so to me in the past.

If you are trying to compress 20 Gb of data and files into an iso, good luck, the iso will almost certainly be huge in size as well.

I know. My ext3 partition is about 20Gb, but the used space is about 2,5Gb. So Remastersys has to compress 2,5Gb of data and files. I don't know why Remastersys does something with the "empty" 17,5Gb...

---

### Post by Alm4riC on 2009-12-07
Anyone? :)

---

