---
title: "Gparted - does it always take so long?"
date: 2010-01-29
forum: General Help
---

### Post by detroit/zero on 2010-01-29
I have a 700GB external USB HDD I'm toying with in Gparted. I had it set up with an EXT3 partition, but I got sick of using 3rd part apps to access the thing on my Windows boxes. So, I moved a bunch of stuff off it to make some room, shrank the EXT3 partition to around 300GB or so, made a new 400GB-ish FAT32 partition, and moved the leftovers on to it.

Now, I'm at the stage where I emptied out the last 300GB of the EXT3 partition and deleted it, and am resizing the FAT32 partition to fill the disk. Gparted has been running for more than 12 hours so far, and it's still at the "move filesystem to the left" stage.

I realize that 300GB worth of data is a lot of junk to move, and resizing a partition that size takes time.

Is 12+ hours really how long something like this takes, or do you think it screwed up and is just running itself in circles? I'm going to let it run over night while I sleep and hope for the best.

---

### Post by tom4everitt on 2010-01-29
Sounds like it screwed up. At any rate backing up your 300 gb somewhere else and reformatting the drive from scratch would be much faster.

---

### Post by detroit/zero on 2010-01-29
> **tom4everitt said:**
> Sounds like it screwed up. At any rate backing up your 300 gb somewhere else and reformatting the drive from scratch would be much faster.
Well, yeah, no kidding. If I had the room to do it, I would have.

Actually, though, it finished during the night. 14 hrs 55mins total time.

---

### Post by c0mput3r_n3rD on 2010-01-29
Could be a power supply issue.

---

### Post by audiomick on 2010-01-29
> **detroit/zero said:**
> Well, yeah, no kidding. If I had the room to do it, I would have.

Actually, though, it finished during the night. 14 hrs 55mins total time.

Good that it finished. It sounds too slow to me, but I am not really an expert.

---

### Post by detroit/zero on 2010-01-29
I think rather it was just the size of the volume, the fact that there was a lot of data to move, and that it was being done via USB on a laptop.

---

### Post by c0mput3r_n3rD on 2010-01-29
> **detroit/zero said:**
> I think rather it was just the size of the volume, the fact that there was a lot of data to move, and that it was being done via USB on a laptop.


Oh yeah if it's a laptop it wouldn't be power supply. That is alot of information to go through!

---

### Post by lavinog on 2010-01-29
If you shrink it to where the free space is limited, it will take a long time.
Always make sure you have 10% free space.

---

### Post by audiomick on 2010-01-29
> **detroit/zero said:**
> ... and that it was being done via USB on a laptop.

Ah, didn't notice that....

---

### Post by oldfred on 2010-01-29
Are you sure you want that large of a partition as FAT. Even Microsoft does not recommend it.

NTFS and Fat info:
[http://technet.microsoft.com/en-us/l.../cc938932.aspx](http://technet.microsoft.com/en-us/l.../cc938932.aspx)
[http://technet.microsoft.com/en-us/l.../cc940351.aspx](http://technet.microsoft.com/en-us/l.../cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
max file size - 4GB minus 2 Bytes

---

### Post by SecretCode on 2010-01-29
I think USB was the real constraining factor. But in general, yes, gparted can take many hours.

---

