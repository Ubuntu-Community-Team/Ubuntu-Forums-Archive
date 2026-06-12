---
title: "Getting your install just right, then backing it up to img"
date: 2009-09-15
forum: General Help
---

### Post by morganpatrick on 2009-09-15
Hey,

I am reinstalling a friend's os (xp) and I had the idea of getting it just right and then making a "snapshot" of the fresh os with all her programs and settings. That way when her computer gets screwed up again she could just boot from a cd or dvd and it would overwrite her hard drive with an image of how it was when it worked well.

I run Ubuntu, and I figured this might be easer to do from linux. I could use dd to get the image and then I could put this image on a DVD if it will fit, but is there a way to get the DVD to automatically overwrite the hard drive? Is there already a program or live disk out there to do this?

Thanks.

---

### Post by winotree on 2009-09-15
I'm thinking that Clonezilla [http://clonezilla.org/](http://clonezilla.org/) will do that regardless of OS.  ;)

---

### Post by morganpatrick on 2009-09-15
This is great. I'll try it. Thank you!

---

### Post by winotree on 2009-09-15
:)

---

### Post by morganpatrick on 2009-09-17
It looks like it worked. The other nice thing about clonezilla is that it appears to have only stored the actual data in the image file. I had 5 gigs of data on a 40 gig hard drive and my img file is 5 gigs. Other programs will img all the zeros...

Anyway I have not tested backing this up yet but when I do, if it works, I'll mark this thread as 'solved'.

Thanks again.

---

### Post by fisheater on 2009-09-17
I searched for this and didnt find any slamdunk info:

I want to back up my HD (with both my WinXP and Ubuntu partitions). Can I image the HD or do I need to make an image of each of the partitions independently?

Thx!

FE

---

### Post by canam101 on 2009-09-23
> **fisheater said:**
> I searched for this and didnt find any slamdunk info:

I want to back up my HD (with both my WinXP and Ubuntu partitions). Can I image the HD or do I need to make an image of each of the partitions independently?

Thx!

FE

You can do it either way.

---

### Post by ezsit on 2009-09-23
I find this tool to be excellent for backing up a complete installation. The benefit is the backup is a live cd/dvd with all the settings intact (as long as the backup can fit on a 4GB DVD disc). You can then reinstall from the live cd/dvd just like you did with Ubuntu.

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

