---
title: "CD/DVD Burning"
date: 2010-06-13
forum: General Help
---

### Post by John_Smith1 on 2010-06-13
OK, so I have little idea how to use either of the 2 Burning apps I have installed with Ubuntu. Brasero Disc Burner, and Disc Burner. Of course coming from Windows, I used Nero, which was good for me, and I could use it. I have archives which would just about fill a DVD (~4.7GB capacity). I dragged and dropped an archive into both programs, but it says something to do with the ISO image file being too large (over 2GB). I don't want to burn an ISO Image, I want to burn data to DVD, which is the option I chose...

Am I doing something wrong? Also, what *do* I do to burn my >2GB <=4.7GB archives to DVD? :confused: Links to downloads, and install commands very-much appreciated!

Thanx...

---

### Post by B-80 on 2010-06-13
I remember when I first switched I had trouble with brazero as well. I switched to K3b which I've had no trouble with.

open terminal: sudo apt-get install k3b

---

### Post by claracc on 2010-06-13
You can use brasero: From aplications menu you select sound and video and disc burner brasero.

In the page of creating a new project you select data project, then you add the files you want to burn with edit, add files. When the files have been added you burn them to a blank disk you have introduce in your optical drive.

Brasero works ok for burning data.

---

### Post by John_Smith1 on 2010-06-13
> **claracc said:**
> You can use brasero: From aplications menu you select sound and video and disc burner brasero.

In the page of creating a new project you select data project, then you add the files you want to burn with edit, add files. When the files have been added you burn them to a blank disk you have introduce in your optical drive.

Brasero works ok for burning data.

OK, but it tells me that files over 2GB are not supported, and about ISO Imaging. :confused:

> **B-80 said:**
> I remember when I first switched I had trouble with brazero as well. I switched to K3b which I've had no trouble with.

open terminal: sudo apt-get install k3b

Think I'm about to try this.

---

### Post by claracc on 2010-06-14
> OK, but it tells me that files over 2GB are not supported, and about ISO Imaging. 

It is an odd thing, perhaps the media you want to burn to don't support more data than 2 Gb?.

This link explains to you how to burn data with brasero: [http://www.linux.com/news/software/applications/280100-using-brasero-for-data-backup-and-iso-burning](http://www.linux.com/news/software/applications/280100-using-brasero-for-data-backup-and-iso-burning)

I hope it can help

---

