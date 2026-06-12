---
title: "Resizing /home"
date: 2010-07-11
forum: General Help
---

### Post by WinterRain on 2010-07-11
When I installed ubuntu 10.04, I did not have a separate /home partition. I had just / and swap. So how do I go about resizing /home when it is just part of 1 big partition? Is it possible without reinstalling?

---

### Post by Chame_Wizard on 2010-07-11
In the live CD when you are in the disk set-up,choose for the *specify partitions manually * option.

There you can safely create a */*(I have 10% of the hard disk),*home* and SWAP partition(the mount points).

Use Gparted to resize your / only partition.

---

### Post by drs305 on 2010-07-11
Here is one method of creating a separate /home partition I've used in the past. You don't have to reinstall but you will need to perform the actions from the LiveCD, since your Ubuntu install can't be mounted when changing the partitions.
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html")

---

### Post by WinterRain on 2010-07-11
> **drs305 said:**
> Here is one method of creating a separate /home partition I've used in the past. You don't have to reinstall but you will need to perform the actions from the LiveCD, since your Ubuntu install can't be mounted when changing the partitions.
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html")

Thanks for the quick reply. From the article: *Note, that resizing and moving partitions is a time-consuming process – it may take hours, depending on the size of your partitions, so reserve enough time for this operation.* Plus a bunch of other operations are needed.

Seems to me, I'm better off reinstalling, since I can get back to where I was in less than 2 hours total. I just need more than the 20gb that is allocated to home when you let ubuntu do all the work. Cheers.

---

### Post by drs305 on 2010-07-11
Unless you have slow Internet speeds or have download limits, reinstalling is often the easiest method and can take less time than moving partitions around. This is especially true if you don't have to recreate a lot of tweaks you have made to an installation.

---

