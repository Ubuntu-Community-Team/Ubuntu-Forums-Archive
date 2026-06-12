---
title: "how much room to leave for home partition/root partition?"
date: 2010-02-07
forum: General Help
---

### Post by rcayea on 2010-02-07
I have finally been convinced to partition my 500GB hard drive from a two partition setup with root and swap to a three partition setup with root, swap, and home. I found a nice tutorial about how to do this, but here is my question:

A) How much space do I leave for the root partition and the home partition?

thanks,
Randy

---

### Post by tubasoldier on 2010-02-07
I've never gone over 8GB in /
But if you are installing a lot of software ouside the regular repositories you may want to go higher.

---

### Post by rcayea on 2010-02-07
thanks for the reply. would you say 15gb is sufficient for root?

---

### Post by jmszr on 2010-02-07
rcayea,

I gave / 15GB and have used 9.7GB (with a fair amount of software installed). 15GB will give you plenty of room and then you'll not have to worry about it.

---

### Post by hero1900 on 2010-02-07
i think for root 6GB is enough just leave the rest to the home and you should always clean and remove old packages
it really depend on your case if you use so much software and where do you install them

---

### Post by kidux on 2010-02-07
I usually use 10-15GB for /, double my system RAM for Swap, 2GB for /boot, and the rest for /Home.

---

### Post by john newbuntu on 2010-02-07
Yeah 8GB seems more than enough for root partition.  Swap would be twice the RAM, although most of it would be wasted but it is small anyway.  /home depends on what you would want your user(s) to store in there? Music? Video? backups?  Take a guess at all these and add it up.  Keep a minimum of 20GB for that.

Ideally, create blank partitions after /home and the root partition so that you could always expand into those should you run short of space.  So say /dev/sda6 is 20GB and mounts /home.  Create /dev/sda7 that is say 50GB.  This way, you can always expand your sda6 if it runs out of space.  Same goes for root partition.
Now, with these blank partitions, you could even install another version of OS and delete it if you are not satisfied.
If you dual boot with windows, you can create another NTFS partition for data sharing between Win and Linux.

PS: I have the whole thing in 5 GB!

---

### Post by rcayea on 2010-02-07
Thank you for all the responses. I have decided to play it safe, I am not a gambler, and I will give / 15gb. 

Thanks again awesome community!

---

