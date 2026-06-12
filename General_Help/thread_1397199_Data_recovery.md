---
title: "Data recovery"
date: 2010-02-03
forum: General Help
---

### Post by ok_dr on 2010-02-03
I've done something stupid. 
I wanted to create in my external hard drive a 10 gb partition with fat32 filesystem in it (to be able to occasionally get something from mac which doesn't write to nfts).
I had not done any partitioning before, apart from when I installed Ubuntu and it looked easy with Gparted, just resize it then format the unallocated space to fat32. But then it showed 5 hours left for the resize, which in 6 hours became 10 hours left so I decided to cancel. Now I can't mount the hard disk anymore and the stupid that I am I didn't back up the data in it.

Please help.

---

### Post by Purplecatty on 2010-02-03
](*,)  Have you tried using LiveCD to boot up to desktop and check if you still have some precious files in the drive which you want to back it up.

Just suggestion

Catty

---

### Post by ok_dr on 2010-02-03
> **Purplecatty said:**
> ](*,)  Have you tried using LiveCD to boot up to desktop and check if you still have some precious files in the drive which you want to back it up.

Just suggestion

Catty

I'll try (later, don't have the live cd now) but I don't have much hope. I can use my computer all right, it's just my external USB hard drive (500gb My passport essential Western Digital)that it doesn't see anymore and being the same system as in the live cd it shouldn't make any difference I guess.

---

### Post by bumanie on 2010-02-03
Shrinking partitions can take a long time as every byte of data has to be moved to allow for the extra space to be created. Stopping an operation like that has probably destroyed the filesystem. Try the live cd as suggested, otherwise you can try something like photorec to try and retrieve important files. Photorec, despite its name can find 100+ file types (not just photos) and is filesystem independent, as in it reads from the raw disk. Photorec is part of the testdisk program - it can be installed in ubuntu > sudo apt-get install testdisk  and to start photorec > sudo photorecor if your ubuntu is not working you can [go here]("http://www.cgsecurity.org/wiki/TestDisk") and download a live cd - tutorials are also available on that site, which you should read before trying to recover anything.

---

### Post by ok_dr on 2010-10-12
In case somebody cares, or has the same problem, I wasn't able to find any Linux tool to help me. Test disk recovered some files but still less than 10%.
Anyway I turned to Windows software and I found several programs who could do the job. Of course none were free, but I could find torrents with registration keys on the net and I was able to recover everything. :P

---

