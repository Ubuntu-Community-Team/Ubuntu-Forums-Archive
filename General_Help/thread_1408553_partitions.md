---
title: "partitions"
date: 2010-02-16
forum: General Help
---

### Post by rflores2323 on 2010-02-16
I have ubuntu 9.10 installed on one partition and wanted to make 2 other partition. one to be able to put all my video files on that partition and another one for my home folder.

what is the best way and utility to use?  is gparted the way to go on the live CD (or usb stick in my case) and then do the partitions that way?

Total size of HD is 320gb.  how much room is needed for the OS , 4gb?? How much for the home folder, 16gb? 

I know the biggest partition is going to be the last one for my video files which I think should be 300 gb.

Or should I just do two partition and leave my home folder and videos in the same paritions?

is there a good how to around.  found this one which looks easy to follow. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by giammy on 2010-02-16
> **rflores2323 said:**
> I have ubuntu 9.10 installed on one partition and wanted to make 2 other partition. one to be able to put all my video files on that partition and another one for my home folder.

what is the best way and utility to use?  is gparted the way to go on the live CD (or usb stick in my case) and then do the partitions that way?

Total size of HD is 320gb.  how much room is needed for the OS , 4gb?? How much for the home folder, 16gb? 

I know the biggest partition is going to be the last one for my video files which I think should be 300 gb.

Or should I just do two partition and leave my home folder and videos in the same paritions?

is there a good how to around.  found this one which looks easy to follow. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


Hi,

gparted is ok as partitioning tool
I usually have only one partition: if you want separate partitions
I'd suggest 20G for OS and 300 for home and video
(20G is big - an ubuntu system can stay in 4G)

bye
giammy

---

### Post by fuzzyk.k on 2010-02-16
in many Linux installations the basic principle is root 20GB, swap 2 times RAM and the rest is home, in your case i would recommend using gparted or hiren boot cd and trying the partition tools there

---

