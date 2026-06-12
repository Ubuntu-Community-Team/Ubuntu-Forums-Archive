---
title: "imaging drive"
date: 2009-11-30
forum: General Help
---

### Post by sandyd on 2009-11-30
I noticed that my laptop was running a bit low on space, so i went out and bought a second hard drive caddy for my dell laptop (has two hard drive holders, one without the caddy)
 Decided to get a 250GB SSD to put in it.

Now heres the problem.
the origional drive (still in hard drive caddy #1) has some really bad sectors on it (esp at the front, had to move the mbr around to get it working), so im planning on replacing it with another one. 

Im going to now be using the 250GB as my main drive, and stick my home partition and the rest of the space-taking-up stuff on the new 1 TB drive im putting in tomorow.
How do i image the current hard drive (160GB) and copy it to the 250GB? (without the home partition, i got a ESATA port so im going to use that to transfer my /home and other files.)

the Operating systems on the current 160 are Windows 7 and Karmic.
Im planning on keeping the windows 7 partition size the same and extending the size of the ubuntu partition

---

### Post by john newbuntu on 2009-12-01
I am not a 100% sure on if this will work. But anyway I hope someone can jump on this and help:
1. Use swapoff to disable swap.
2. Use the dd command to copy everything from hda to hdb.
3. Switch your disks.
4. Create a new ext3(or ext2?) filesystem on the other disk with a /oldhome partition
5. Swap the /home partition with /oldhome by playing with /etc/fstab
6. copy files over from /oldhome to /home
7. get rid of the /oldhome from /fstab.
My concern is that the dd command working properly with bad sectors in the old disk.

---

### Post by StuartN on 2009-12-01
You can download and burn a Clonezilla CD that will guide you through the process of imaging the first drive on the second, then swap them over- there will be no change to the first drive, so it is a backup if the procedure does not work. (It worked a charm for me when I replaced my drive).

---

