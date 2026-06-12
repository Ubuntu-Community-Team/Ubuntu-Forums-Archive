---
title: "Encrypted /home partition and running out of space..."
date: 2010-05-26
forum: General Help
---

### Post by bag123 on 2010-05-26
Folks,

Need to get a little help here, so would be grateful for a couple of minutes of your time.

I have an Acer Aspire One, Model ZG5 (also known as the 110 with 8GB SSD) which originally came with Linpus Lite installed on it.

I previously had 9.10 installed which was great, but I've done a fresh install of UNR 10.04 since I had a full /home partition and wanted to set up with more space.  

This time, I opted for a larger /home drive (~4GB) and also to have it encrypted, which is a good idea for netbooks given their portability (and I have no idea why I didn't do it before!).  Since I had very little space on my 8GB drive (if I wanted a larger /home) then I installed /home onto a separate partition, which is located on a 16GB SD card which lives in my machine permanently.

Installation was a breeze, and encryption seems to work fine.  I have verified it and it seems to be working.  However, I've now hit two related problems - one of which is to do with Thunderbird, and one which is an issue with the encrypted /home drive.

Firstly, I have a large gmail account which I like to replicate offline in Thunderbird (am using v 3.0.4).  My online gmail tells me that I'm using 1.4GB of data space online.  Using the old T'bird (v2.whatever) my offline T'bird storage was approximately the same size.  This is not now true of my current offline storage file size, which is showing at 3.2GB for the same data.  I started with a clean slate, just installing T'bird, setting up my account and then leaving it to download all data from Google.  

Anyone know why this offline size is so much bigger than the online storage size or even the previous offline storage size?

Secondly, the encrypted /home drive.  Given that I needed I put this on a separate card and partition, I had hoped to escape any issues with not having enough space.  However, my system is now telling me that /home is out of space...

Specifically, I can see that I have used 3.6 of my 3.8GB storage for /home.  This is due to the large size of my offline storage folder.

As I see it, I need to do one of two things (possibly both) - reduce the size of my offline e-mail storage, and increase the size of my /home partition.

Reducing the offline storage will be about finding out why it's so big in the first place.  

However, if I wanted to increase the size of my encrypted /home file how would I do this?  I have used gparted to make additional space after it - so I could increase the size if it's possible, but I am a little concerned.

If I just increase the size of the partition, would this work?  Are there issues with the fact that it's an encrypted partition?  What should I be aware of if I wanted to increase an already in-use partition, and how should I best go about this?

Do I need to do it from a live USB image?  What is the best way to achieve this?

Many thanks in advance for your help.

Bag123.

---

### Post by freddiespagheti on 2010-05-26
1. I'm not sure about why the offline size is bigger but my first guess is that it's because your drive is now encrypted so each file takes up more space than it did originally. (This may be inccorrect, it's just a guess)

2. I don't think gparted would have an issue resizing an encrypted partition (again I may be wrong) but I'm pretty sure if it wouldn't work, then attempting it wouldn't hurt anything at all. It would just give you an error message and give up. (This also may be incorrect so wait for someone else to verify it before you try it)
You should also try googling 'resize encrypted partition' and other similar phrases and see what comes up.

---

### Post by bag123 on 2010-05-26
Thanks FreddieSpagheti,

OK, will have another look online and then give it a go.  

Anyone else got any ideas about this one?

Thanks,

Bag123.

---

