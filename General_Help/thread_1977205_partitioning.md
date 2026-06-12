---
title: "partitioning"
date: 2012-05-09
forum: General Help
---

### Post by bofak on 2012-05-09
Which forum or other info source should I visit for basic (fairly noob) discussion of partitioning?

How many partitions is it useful to have, and what size?  There seems to be a school of thought that doesn't favour partitions at all.  And swap-files -- yes or no?

I want to inform myself on all this kind of stuff.

---

### Post by jadtech on 2012-05-09
unless you are installing a server  OS  you only have need for 2 partitions really  / (root) and  swap  some like a third for home partition  though  its not completely necessary  for just learning ..

if you want just 2 partitions to start over all 30 to 50 gb is a good start 

you make the free space boot up the live boot cd go to Gparted and  make one big extended partition in side that you need ext4 partition of nearly all the space leave 2 gb and make that your swap .. 

if you want the 3 partitions the / root would be 6 to 7 gb ,  the rest would go 2 gb swap and the rest  /home .. 

if your building a server there are many more you could add that is a whole other system and set up ..

you can check this link for more detail with some pictures  to guide 
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by cortman on 2012-05-09
+1 for being interested in learning.
[Here's]("https://help.ubuntu.com/8.04/installation-guide/hppa/partition-sizing.html") a good starting point for you.

EDIT: Re jadtech- no partitioning scheme is gospel - it's really a personal choice. I wouldn't make size recommendations until I knew the HDD size.
Decent advice for a noob though.

---

