---
title: "Many partitions as one"
date: 2009-09-05
forum: General Help
---

### Post by El Pinguino on 2009-09-05
I recently got a large hard drive and dropped it into my ubuntu (htpc) machine. I partitioned it (in 4: media1, media2, media3, media4) and now I'm sort of wishing that I could see everything as one drive (media). And I wish that the mounting points that I created (media1 etc) don't appear on the desktop.

In other words, I'd like to have one icon on the desktop that, when clicked, opens a folder which gives access to all the media in all the partitions in the new drive.

I suspect my solution lies in changing the mounting that I have in /etc/fstab and perhaps something to do with hard/symbolic links.  Unfortunately, I'm too inexperienced to really know what will work or whether to pursue it.

Suggestions?

---

### Post by plucky on 2009-09-05
> **El Pinguino said:**
> I recently got a large hard drive and dropped it into my ubuntu (htpc) machine. I partitioned it (in 4: media1, media2, media3, media4) and now I'm sort of wishing that I could see everything as one drive (media). And I wish that the mounting points that I created (media1 etc) don't appear on the desktop.

In other words, I'd like to have one icon on the desktop that, when clicked, opens a folder which gives access to all the media in all the partitions in the new drive.

I suspect my solution lies in changing the mounting that I have in /etc/fstab and perhaps something to do with hard/symbolic links.  Unfortunately, I'm too inexperienced to really know what will work or whether to pursue it.

Suggestions?


Why not just have one large partition and create 4 folders within the partition for your different media requirements.Linux treats partitions as folders anyway.

Good Luck

---

### Post by El Pinguino on 2009-09-06
> **plucky said:**
> Why not just have one large partition and create 4 folders within the partition for your different media requirements.Linux treats partitions as folders anyway.


Unfortunately, it was the result of lack of foresight.  Or perhaps just bad luck in my decisions.  

At the store, as they guy handed me the drive he asked, "How many partitions are you going to have?" (it's a 2GB drive).  I hadn't considered partitions since it's essentially one use but it got me thinking.

I was under the impression that partition size had an influence on block size and if I wanted to keep this manageable then perhaps I should have smaller partitions.  This may have been inaccurate/outdated info from my Windows days.

In addition, there are various other arguments to be made for partitioning. And I was swayed and made several partitions.

Now all my media is there and it would be troublesome to move it all off while removing partitions. So I was looking for another option.

Part of my wish was to have something that all the family could navigate in a user friendly fashion. This could probably be managed with what I was suggesting.

On the other hand, mounting a folder with sym/hard links to the media might be good for viewing/playing the media but not so good when I wanted to add new media to a particular partition.

:(

I guess I may have to mess with re-partitioning larger again.

---

