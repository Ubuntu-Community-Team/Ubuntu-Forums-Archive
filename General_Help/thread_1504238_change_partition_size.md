---
title: "change partition size"
date: 2010-06-07
forum: General Help
---

### Post by cdude42 on 2010-06-07
Ok so i got my laptop to run ubuntu after some difficulty with my GPU, i gave ubuntu a small partition when i installed it, but now i want it to be 100 Gigs. so how can shrink my windows partition and make the ubuntu partition grab the extra space?

---

### Post by Mecasickle on 2010-06-07
Any one out there who can give us the answer?

'm habving the same problem like for about 2 months.

Thanks!

---

### Post by bumanie on 2010-06-07
To shrink windows - right click my computer --> Choose manage and then choose (I think - long time since I've done this) --> Storage --> Disk management (or some words to that effect). Right click the partition you wish to shrink and you should have a window come up that allows you to shrink it. [COLOR="Red"]You should defrag windows partition at least twice prior to shrinking and copy/backup any important data just in case something goes wrong.[/COLOR] 
To increase the partition, boot a live cd --> in terminal > sudo gpartedand the gparted gui should be easy to work out how to use it. If not go [here]("http://gparted.sourceforge.net/docs/help-manual/C/gparted.html").

---

### Post by bumanie on 2010-06-07
Oh...just found [this]("http://tips4pc.com/format%20your%20computer/how_to_shrink_a_partition_on_you.htm") that is showing what I have described - this is the vista gui, but it works the same on xp and win 7 as far as I know.

---

