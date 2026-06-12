---
title: "lost partition table, no magic superblocks - how to get the data?"
date: 2006-05-02
forum: General Help
---

### Post by justleen on 2006-05-02
Hey there folks!

I'm a bit at a loss at the moment. I've managed to lose the partition table  of one of my harddrives. The irony dictates that only two days before i decied to use this drive for /home, my music and my photos (all the stuff that matters really). 
Now ive tried several ways of restoring a backup superblock (lots info on the internet for that) but every time i try, i get the message back that theres no info stored in this blocl (not a valid magic superblock).
So i installed Testdisk, a nifty tool which should allow me to restore the partition table.. I followed the instructions, and all seemed well. Test disk advied i should correct the number of heads on the drive, and the block size.
It even gave me the location of the magic superblocks. 
Great! i thought. 
but..
The changes i make in testdisk dont get saved for some reason, and the given backup blocks  give me the same error: not valid magic superblocks.
Its seems that due to an incorrect block size, the location of the superblocks is incorrect (i've created deafult EXT3 partitions, what would normaly be the blocksize under ubuntu, 4096?)

Now, i can see my files using testdisk, but im not able to access them
At this point, i dont care about restoring the partition table any more, i just want to be able to backup my data.

Does any one here have any idea how to copy files from a drive that has no partition table? Any restore tools perhaps?

Any help would be greatly appreciated

---

### Post by Sef on 2006-05-02
Download one of these.

Ultimate Boot CD

[http://www.ultimatebootcd.com/index.html]("http://www.ultimatebootcd.com/index.html")

System Rescue CD

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by elamericano on 2006-05-02
[QUOTE=Sef]Download one of these.

Ultimate Boot CD

[http://www.ultimatebootcd.com/index.html]("http://www.ultimatebootcd.com/index.html")

System Rescue CD

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")[/QUOTE]

You seem to have left out a step or two, Sef. :-k 

Justleen, It looks like you found a great tool with good documentation. I haven't used it myself, so I couldn't guess about saving properly, but your block size is almost always 512 bytes. The disk does whatever it wants internally, but with Logical Block Addressing, blocks are half a K.

---

### Post by justleen on 2006-05-02
Thnx guys.. the bootCD's ar eno option, since they both assume you have working partition table in place.. which i dont have.. :(

The author of testdisk is offering his email address for when you're really stuck, so i send of the logs to him and im crossing my fingers until i hear of him...

---

