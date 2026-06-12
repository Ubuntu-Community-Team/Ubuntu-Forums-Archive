---
title: "Mount incomplete gddrescue image"
date: 2012-02-26
forum: General Help
---

### Post by yyann on 2012-02-26
Dear folks,

first I'd like to thank you for checking this thread and thus caring. :)

I'm at a friends whose 640 GB harddrive has arrived at the **click-of-doom state**. Interestingly, for some reason we were able to mount it in an Ubuntu 11.10-Live-CD environment yesterday, just long enough to run **gddrescue** and recover 293.2 GB of a 340 GB partition before it **went dead again** - this time for good, it seems. Now, since ddrescue did not finish and I do not have a valid image file, I fail to mount it. It is not recognized as a valid filesystem. Here's what happens when I try "mount":

```
sudo mount -t ntfs -o r,force,loop,offset=8192 /media/BackUp/EIGENSAV.img /mnt/EIGENSAV/
NTFS signature is missing.
Failed to mount '/dev/loop1': Invalid argument
The device '/dev/loop1' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```Mark that I have no idea of the actual offset, I can only guess.

Do you know any way in which I can mount this incomplete image or at least retrieve the data stored in it? It is bound to be broken, but we should have around 85 % of the files in that image, am I right?

Thank you for your invaluable assistance.

Yours
Yann.

P.S.: Yes, I have repeatedly scolded my friend for not maintaining a backup of his disk.

---

### Post by yyann on 2012-02-29
Uh oh... I assume 150 views and zero response gives us a real problem?

---

### Post by Khayyam on 2012-02-29
> **yyann said:**
> Uh oh... I assume 150 views and zero response gives us a real problem?

I think so ... when ddrescue makes an image it will copy bad sectors, everything, but if it doesn't complete you will have nothing, at least nothing resembling a filesystem.

I've not attempted this but you might try running ddrescue on the (incomplete) image, its a long shot but it might be able to make an image of that portion of the drive that was rescued. Sorry, but that's about I can think of.

BTW, you shouldn't mount, ddrescue works like 'dd', the drive doesn't need to be mounted for it to be imaged, infact, its better not to.

best ... khay

---

### Post by audunpoi on 2012-07-10
Hi. Don't know if you solved this already. I found this post since I had a similar problem. I made a very incomplete image with ddrescue but were able to get my files from it with photorec. Photorec recovers lots of filetypes, not just pictures. Unfortunatly filenames are not restored. 
Install testdisk, then run: photorec name_of_image_file
You can also try to run: testdisk name_of_image_file to recover partitions.Actually, try that first..

---

### Post by Nixarter on 2012-07-10
When that happened to me, I just let DD run.  I put mine in an external case and kept it cool with fans (dunno how much that helped...).  Whenever it would fail and start clicking, I would do a hard reset on the drive.  DD is set up to keep waiting for the drive to come back.  When it does, it gets what it can until it fails again, then waits... again.  It took hours but I was able to get over 99.9% of a 30gb partition back by doing that (some was corrupted before the drive started clicking).  Other programs (GUI ones) would see the drive drop and then they would fail and save.  SOOOOO annoying!

Anyway, after that I used **testdisk** to mount and recover the files from the image, because dd wouldn't do it.  It worked, though it was a bit of a pain to go through in a terminal.

edit: just realized this thread was necro'd :o

Ohh, well. Someone may find the above info useful.

---

