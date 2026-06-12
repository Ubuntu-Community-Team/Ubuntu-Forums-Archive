---
title: "Help with Gparted"
date: 2009-11-24
forum: General Help
---

### Post by Alan502 on 2009-11-24
Please! help me to deal with Gparted. I already screwed it up once and i had to format all my drive, losing part of my data; and i dont want that to happen again!
Ok so this is the screen shot of my Gparted (sorry for the blank space but im not too good with gimp!----  ok thanks mechro for fixing my image :) )

[IMG]http://i50.tinypic.com/348htgx.jpg[/IMG]

basically i want to do three things:

1. Move the swap partition (sda4) to my etx3 partition (sda3). That way sda4 will be a logical partition in sda3.

2. As you may have noticed, for some reason a logical partition(sda5) is occupying its whole primary partition (sda2). This is useless and might decrease the performance so i want to move all the data from sda5 to sda2, and delete sda5 when it is empty. That way i would eliminate having any useless logical partitions.

3.Make a logical partition under sda1, about 10GB.

Thanks for your help, it will be very appreciated. :)

---

### Post by mechro on 2009-11-24
Please could you edit your post to either include the following image or at least delete your linked image...



Thanks.

---

### Post by Alan502 on 2009-11-24
Done mechro, thanks for the correction :) any ideas with what i want to do?

---

### Post by mechro on 2009-11-24
sda2 is an extended partition which means it's not a partition in its own right that you can put files in. In other words you can't boot from an extended partition and you can't save files to it. It's just a scheme to hold logical partitions, in your case sda5 takes up the whole of the extended partition. There's nothing wrong with that but you could also have an sda6, sda7, etc, etc in the extended partition if you so desired. You would have to resize sda5 to accommodate these extra partitions.

If you tell me which partitions contain data you wish to save I'll have a think of a suitable scheme.

---

### Post by Alan502 on 2009-11-24
Well, all partitions, but the swap partition, have data i'd like to save. Is this a problem?

---

### Post by mechro on 2009-11-24
Well, you're probably going to have to stick with the extended sda2 partition unless you've got somewhere else to save data. Using Gparted you can't make sda2 a Primary partition ("move all the data from sda5 to sda2, and delete sda5 when it is empty") without first deleting sda5.

Also, "Move the swap partition (sda4) to my etx3 partition (sda3). That way sda4 will be a logical partition in sda3." is impossible. You could make a logical partition, say, sda6 in sda2 and put swap there.

What is in sda1? I can't see much from the graphic. sda1 is a primary partition, you can't make it a logical partition under your current scheme. Also, if you're booting Windows from there it has to stay as a primary partition.

---

### Post by Alan502 on 2009-11-25
Yeah, i am booting windows from sda1. Well, i think that what i want to do cant be done with gparted. I wanted to use that utility since it is open source and more reliable. There is a windows utility that i used tho, that can do most of the above.I think i'll go back just to edit those partitions. Anyway, thanks for your help! ++

---

### Post by mechro on 2009-11-25
It's not that Gparted does any less than most other Partition managers, it's just you seem to be misunderstanding the difference between Primary, Logical and Extended partitions.

This is quite a straightforward explanation...

[http://wiki.wolvix.org/Partitioning](http://wiki.wolvix.org/Partitioning)

---

