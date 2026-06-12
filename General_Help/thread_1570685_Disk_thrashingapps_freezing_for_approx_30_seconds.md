---
title: "Disk thrashing/apps freezing for approx 30 seconds"
date: 2010-09-08
forum: General Help
---

### Post by kitchens on 2010-09-08
Hello,
I've been having this issue since at least 9.10. I'm randomly encountering disk thrashing and application freezing which lasts around 30 seconds. Some applications seem to encounter this more often than others. Firefox and Picasa are pretty reliable at reproducing the issue. It also happens often when I'm using Transmission. CPU usage is not unusually high during the 'thrashing' sessions. Running iotop hasn't shed any light on the problem either. I was wondering if anyone else has encountered this or maybe someone could give me some clues. 
I'm running a dell inspiron 530 with ubuntu 10.04 64bit. I have 4gb of ram. Here is my 'df -h' if that is helpful. 


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             103G   26G   73G  26% /
none                  2.0G  288K  2.0G   1% /dev
none                  2.0G  1.1M  2.0G   1% /dev/shm
none                  2.0G  232K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sdb1             459G  224G  212G  52% /home

Any help is appreciated. 
Thanks.

---

### Post by ajgreeny on 2010-09-08
Apart from a huge root partition usage, (of 103GB, 26GB are used), I can see nothing unusual in your **df -h** figures.

But what on earth is using all that space in root?  My root partition takes only 3.6GB, so 26GB for yours seems excessively large, and I wonder if that has anything to do with the disk activity.

---

### Post by kitchens on 2010-09-08
I have a 20gb truecrypt file on the / drive. It used to be on my /home drive but I moved it recently.

---

### Post by ajgreeny on 2010-09-08
> **kitchens said:**
> I have a 20gb truecrypt file on the / drive. It used to be on my /home drive but I moved it recently.
Is it possible that this could be the reason? I have never used or even seen any disk encryption in action, so I ask the question from a position of total lack of knowledge.

---

### Post by kitchens on 2010-09-08
I really don't think this is related for several reasons. 
1. The encrypted file is not opened or mounted. 
2. I had the same problem when the file was on another drive. 
3. I had the same problem before the truecrypt file even existed.

---

### Post by dcstar on 2010-09-09
> **kitchens said:**
> Hello,
I've been having this issue since at least 9.10. I'm randomly encountering disk thrashing and application freezing which lasts around 30 seconds.
..........

Get a new hard disk that doesn't have bad blocks which cause constant retries when the system hits the faulty area?

---

### Post by kitchens on 2010-09-09
> **dcstar said:**
> Get a new hard disk that doesn't have bad blocks which cause constant retries when the system hits the faulty area?

I've run 'badblocks' on both of my drives and neither of them returned errors.

---

