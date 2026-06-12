---
title: "Flash Drive Help?"
date: 2011-05-25
forum: General Help
---

### Post by djb6 on 2011-05-25
This is probably really easy, but I seem to have a problem with my flash drive.  I bought it at the store as a 4gb flash drive.  I turned it into a bootable flash drive with a 2gb program on it (ChromeOS).  That isn't working so I was going to try it again.  Only problem is now the flash drive isn't saying it's 4gb, it's saying it is 250 mb and I don't know how to reset it.

Any help would be great!

Thanks!

---

### Post by djb6 on 2011-05-25
Downloaded Gpart and now I can look at all the different partitions but I don't know what to do from there to get it back to the 4gb it started out as.

---

### Post by LordNeo on 2011-05-25
Use the disk utility to check the disk, unmount and wipe it entirely.
You will find it already installed.

Best regards

---

### Post by djb6 on 2011-05-25
Alright, one more time as to what I did.  I was able to clear data from most of it, but now I'm stuck with two partitions and I really want one.  I have two fat16 partitions.  One is 3.48 gb and the other is 250 mb.  Any way to get those to become one?  I tried to just click delete on both but on the little one, the delete word is blacked out.

---

### Post by LordNeo on 2011-05-25
> **djb6 said:**
> Alright, one more time as to what I did.  I was able to clear data from most of it, but now I'm stuck with two partitions and I really want one.  I have two fat16 partitions.  One is 3.48 gb and the other is 250 mb.  Any way to get those to become one?  I tried to just click delete on both but on the little one, the delete word is blacked out.
In the disk utility you will find 2 options to delete partitions, one above the "Disk Graph" and another below. The above will delete the whole drive and define a new filesystem so you will be able to redo as many partitions as you want

---

### Post by backu on 2011-05-25
Using the disk utility, you should be able to 'format drive', which is different than formatting the volume, and should be able to create 1 partition using the tool.

---

### Post by LordNeo on 2011-05-25
See the screenshot, it will point out what we are saying.

PD: Sorry i'm using ubuntu in spanish

---

### Post by djb6 on 2011-05-25
Yeah I got it.  Thanks for the help.

---

