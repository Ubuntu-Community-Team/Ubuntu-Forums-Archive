---
title: "Messed things up with rsync"
date: 2012-02-15
forum: General Help
---

### Post by barbolanero on 2012-02-15
So, here's the deal, a friend taugth me to use rsync and he left me written how I should use it as:

rsync -avh --delete user@100.100.100.100: ~/Source/ ~/Destination

So far there was no problem, and I had been using it for some time, although it was with identical folders always... until today. I needed to bring some files to my laptop and I used it with the following source and destination:

~/Downloads/Source/ ~/Downloads

And here is when I messed up I'm guessing, since it deleted everything I had on destination (I know, silly me not realising it would go that way) and I lost over 20gb of data. 

Is there any way I can reverse the damage and retrieve those files? Please let me know ASAP. 

Thanks.

---

### Post by trollger on 2012-02-15
So the question is basically. How do I "undelete" files? and fortunately for you, you are not the first person to accidentally delete a bunch of meaningful data on your hard drive. There is software that will allow you to recover most of to all of your lost data.

Essentially, when you delete a file from your hard drive the data is still on your hard drive some where, the operating system simply ignores the data and it will overwrite it later if needed. The data is most likely recoverable.

In order to "undelete" your files you are going to need to report back what type of partition the deleted data is in. Run 

sudo fdisk -l

and give us the output. If there is more than one drive tell us which one the data was on. In the mean time don't panic or make any major changes to your system.

---

### Post by barbolanero on 2012-02-16
Well, things got weirder, I tried to login today and it just kept throwing me out. tried a bunch of things thinking it was xserver (dpkg-reconfigure and stuff like that) but nothing. My engineers friends are al MIA so I had to run an emergency system reinstall (although I kept the /home partition intact for this). I'll post the outpost later on, but I already tried using scalpel which never finished properly since it didn't had enough free space on hd. Most likely messed up even more by now. Still not giving up.... at least on the hope to learn what to do next time. :(

---

### Post by barbolanero on 2012-02-23
Well, got solved... somehow, by some friends. Thanks anyway.

---

