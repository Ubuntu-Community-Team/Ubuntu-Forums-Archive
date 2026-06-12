---
title: "Any way to fix bad sectors?"
date: 2012-02-14
forum: General Help
---

### Post by Speedwagon on 2012-02-14
My 1TB drive seems to be failing on me.  It is reporting bad sectors, and causing me headaches.  Is there a way to fix this?  Or do I just need to get what data I can off the drive, ASAP?

---

### Post by despuit on 2012-02-14
By definition a bad sector is a sector on a computer's disk drive or flash memory that cannot be used due to permanent damage however there are a few things you can try however it would be recommended you back up your drive immediately and get into the habit of doing this regularly. You can use the FSCHK command to identity errors on the drive and post the output here so someone can provide you more insight on your situation. Additionally you can run*badblocks*and save the bad sectors to a file; then use*mkfs*to make sure the filesystem won't use those sectors.

---

### Post by 23dornot23d on 2012-02-14
Always best to get the DATA off of a drive that starts to show bad sectors IMHO

photos .... code .... etc .....

[http://sourceforge.net/apps/trac/smartmontools/wiki](http://sourceforge.net/apps/trac/smartmontools/wiki)

( See above - it will let you know if it gets any worse .... mine is working but I almost left it too late to recover a lot of photos and Blender work that I did on mine - it keeps reporting more and more bad sectors .... not sure whats caused it ..... wear and tear possibly )

Best safe than sorry .... and drives are relatively cheap compared to the hours of work that could go missing ...... they always say to back up regular .... the bigger the drives get seems we still manage to fill them.

---

### Post by Gremlinzzz on 2012-02-14
How to Fix Bad Sectors in Linux

[http://www.ehow.com/how_7226154_fix-bad-sectors-linux.html](http://www.ehow.com/how_7226154_fix-bad-sectors-linux.html)

:popcorn:

---

### Post by jerrrys on 2012-02-14
> **Gremlinzzz said:**
> How to Fix Bad Sectors in Linux

[http://www.ehow.com/how_7226154_fix-bad-sectors-linux.html](http://www.ehow.com/how_7226154_fix-bad-sectors-linux.html)

:popcorn:


Drexel U. states that this is for ext 2 & 3 file systems.  We are running ext 4

---

### Post by 2048Megabytes on 2012-02-14
Bad sectors on hard drive spread eventually.  Any hard drive with bad sectors is unreliable and on its way to being useless.  Get all the data of the hard drive you value and then destroy the drive.

---

### Post by Speedwagon on 2012-02-15
I've been trying to copy the data off.  But it keeps failing to do so.  If I do a complete copy, the computer will eventually freeze altogether.

Is there another way around this, that will successfully copy the data?  Or am I just screwed?

---

### Post by coldraven on 2012-02-15
A bit more info would be helpful. Is this an internal or external USB and what formatting and partitions have you got?

---

### Post by Grenage on 2012-02-15
> **Speedwagon said:**
> I've been trying to copy the data off.  But it keeps failing to do so.  If I do a complete copy, the computer will eventually freeze altogether.

Is there another way around this, that will successfully copy the data?  Or am I just screwed?

Possibly screwed, possibly not.  You could try using dd_rescue to mirror the drive (or copy the results to an image), or just keep trying to grab individual bits of data as you are.

---

### Post by Speedwagon on 2012-02-15
> **coldraven said:**
> A bit more info would be helpful. Is this an internal or external USB and what formatting and partitions have you got?

Internal, ext4, partitions for windows(that I don't actually use anymore), ubuntu, and /home.

---

