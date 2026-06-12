---
title: "how much root space is needed?"
date: 2010-08-24
forum: General Help
---

### Post by superarthur on 2010-08-24
I am going to create an ubuntu partition just over 200GB
I have 4 GB RAM, so I am going to create 4GB swap
Then I am going to separate the remainder into root and home
Is 10 GB of root enough?
(btw, it's going to be lucid)

---

### Post by sidzen on 2010-08-24
Recommend making / larger if no /tmp partition is planned and one wants to copy DVDs
2XRAM for swap
Remainder for /home

---

### Post by sidzen on 2010-08-24
I recommend:
Making / larger if no /tmp partition is planned (add 5GB) and one wants to copy DVDs
2XRAM for swap (8GB)
Remainder for /home.

---

### Post by superarthur on 2010-08-24
Thank you for answering.
I thought swap is there for people with not enough RAM (i.e. <2GB)
Other than that, I think it is just for hibernation, which requires as much space as the RAM.
Can you give me a number for how many GB I need for root?

---

### Post by roy913 on 2010-08-24
it depends on what tasks do you need to achieve.

while i m the only user of my machine, it is always as simple as: 
/ 20G
/home 30G (encrypted)
/windows 20G (dual boot xp)
/share (the rest of the harddrive, fat32)

All those confidential are kepted in /home
all music, photos & non-important are stored in /share for both xp n ubuntu.

i know mine is not the best way to do it, hope others can offer some better suggestions.

---

### Post by roy913 on 2010-08-24
i have only 1.5G ram and i set my swap size to be 1G, yet rarely use more than 100M..

---

### Post by bryanl on 2010-08-24
The old 2x memory swap size doesn't fit with modern multi-GB memory systems. Unless you really get into graphics or other memory hogging applications, odds are you won't use any of it. 

Another modern change is that swap files are as effective as swap partitions so you can simplify your partitioning by using a swap file (I wonder why Ubuntu doesn't default this way)

I set aside 12 GB for / and the remainder of the available disk space for /home. With Lucid, I am using 6.0 GB of the root partition and that includes a 1.8 GB swap file. That is on an AMD dual core with 1.7 GB memory available. The only time I see the swap file being used (I monitor with GKrellM) is when Handbrake gets a bad input video file. I do some editing of multi megapixel photographs with gimp but even when I load up 20 pics or so at once, the swap doesn't suffer much use.

I have encountered temporary space problems with some apps doing DVD writing. That is usually fixed by setting that applications preferences to use my home directory temp folder for its temporary files. 

Of course, hard drives are large and inexpensive so hassling a few GB here or there really shouldn't be that big a deal.

---

### Post by sidzen on 2010-08-25
Thanks, BryanL, for the up-to-date info regarding swap/swap file.  
I'm using an old 2.4MHz P4 this moment.  It has 512MB RAM.  DVD manipulation, including HandBrake, uses up /tmp quite readily.  
roy913's ". . . it depends" is in order.

---

### Post by uRock on 2010-08-25
The large swap size comes in handy when using the Hibernate function, other than that it is not really needed. The only time my system uses Swap is when I am running more than one VBox or when monitoring the network with Wireshark.

10GB is plenty of space for the /root.

---

### Post by LowSky on 2010-08-25
I usueally go 20GB for /
the rest for /home
No need for swap I've never even use it with 4GB of RAM
Then I have two other hard drives for MythTV storage.

---

### Post by ratcheer on 2010-08-25
I use at least 10 GB for root. 20 GB should be roomy. I think you should have some swap space even if you never see it being used. At least 1 GB, but I still prefer 2 times RAM. With a disk as big as yours, it shouldn't hurt anything.

Tim

---

### Post by superarthur on 2010-08-25
Thanks a lot. I used 20GB for root.

---

