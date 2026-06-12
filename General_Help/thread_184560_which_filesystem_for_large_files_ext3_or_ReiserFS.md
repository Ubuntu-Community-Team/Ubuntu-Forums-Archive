---
title: "which filesystem for large files: ext3 or ReiserFS?"
date: 2006-05-30
forum: General Help
---

### Post by Denis on 2006-05-30
Hi

At the moment I am using ReiserFS for my storage disk, as I thought ReiserFS was the best filesystem for very small and very large files. But looking at [these test result]("http://linuxgazette.net/122/piszcz.html") from The Linux Gazette (January 2006), it seems that ext3 is much faster at creating and copying 1 GB files. 

I have to decide which filesystem I want to use for a harddisk I am buying in the near future. It will be a SATA, 300 GB disk (I may want to make it larger in the future by putting it in a JBOD arrey). It's for storage and it will contain large files (of about 1 GB). 

I want it to be reliable and fast, without losing excessive disk space off cource. Power cutoff won't really be a problem since I use a UPS, but I do want to be protected by the filesystem somehow. 

After reading these tests I'm not sure ReiserFS is good for me. Can anyone give me some advise on which filesystem to use?

Thanks.

---

### Post by frodon on 2006-05-30
The suitable File system for big files is XFS, however i would always recommend ext3 rather than reseirFS because of stability. ReiserFS is faster than ext3 but also less reliable.

---

### Post by Denis on 2006-05-31
I'm thinking of using XFS, since it is really good for large files. 

Is there anyone who has experience with XFS? Are there any options that I should be aware of?

---

