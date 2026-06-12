---
title: "Fastest filesystem for SSD?"
date: 2011-03-19
forum: General Help
---

### Post by blazemore on 2011-03-19
Hi all,
I have just got an SSD (Kingston SSDNow 100v 64Gib)
It supports TRIM, and is definitely one of the better ones available.

I am asserting here that the "limited number of writes" problem is a myth, so I'm not looking for an answer to that.
My question is, what filesystem will help me get the best performance out of my SSD? Bear in mind SSDs excel at random access time, but sequential file performance is meh.

Does anyone have any advice?

---

### Post by blueridgedog on 2011-03-19
I would read up on noatime and nodiratime as mount options as it is likely that you will ultimately use ext3 or ext4.

---

### Post by blazemore on 2011-03-21
I'm using ext4 with noatime in fstab, and it seems to be very quick, especially for things like menu delays and loading thumbnails.

With my mechanical hard-disk, if I had been idle for a while and then loaded a folder full of images, I'd have to wait at least 5 seconds for my hard disk to spin up, and load the images, then as I scroll down I'd have to wait and watch it load the thumbnails one by one.
Now, **bang!** it's all just there!

I really recommend getting a low-capacity SSD. My 64Gib one (Kingston SSDNow 100v) was about £70 so they're really cheap these days as well. Make sure you shop around though, as a lot of them are really not worth getting, especially if they don't support TRIM.

---

