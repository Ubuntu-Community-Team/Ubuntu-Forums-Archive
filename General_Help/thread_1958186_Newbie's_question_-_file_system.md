---
title: "Newbie's question - file system"
date: 2012-04-13
forum: General Help
---

### Post by chenxinghao on 2012-04-13
The System Monitor's File Systems window reports 129 GB Free and 122GB Available. Where does the 7GB that is Free but NOT Available go?

---

### Post by Quackers on 2012-04-13
Just formatting a partition can use up that much space.

---

### Post by chenxinghao on 2012-04-13
That doesn't sound right. Here is the System Monitor's File Systems window reports:

Total: 134.6 GB
Free: 129.2 GB
Available: 122.4 GB
Used: 5.4 GB

The hard drive is 150 GB raw. So after formatting, the total space is 134.6 GB, which I understand.

I am not sure how the other three measures have anything to do with formatting.

---

### Post by jadtech on 2012-04-13
numbers can vary a lot for a few reasons different format types use slightly  more or less space also keep in mind that to format means to map your drive every byte every sector and cluster is addressed that info has to be stored some where ..

 picture your drive as a piece of graph paper , this paper has 132096 tiny square each one representing a single byte each of these bytes is index  with an address so it can be found once in use if you 32 bit typically 32bit each byte has 4 addresses the hD is mapped to know basically where to find each then to make it easyer  the bytes are mapped in clusters and sectors .

the bigger the hard drive the bigger the map , the same goes for ram as well since at boot it to is all formated and mapped the more you have the bigger the map :)

keep in mind mileage may vary depending on the geometry there will be left over space that cant be used depnding one what type of partition... so 150 gb raw is a best case situation ..

---

### Post by chenxinghao on 2012-04-13
I understand the storage overhead of formatting hard drives.

As I have described before, it seems that after formatting the 150GB hard drive results a total of 134.6 GB (usable) space (one partition).

I believe the numbers are measured for the space after formatting.

Total of 134.6 GB (total) = 129.2 GB (free) + 5.4 GB (used)

The number that I don't know how to fit in to this math is the 122.4 GB (available).

Are you suggesting that, in order to use the 129.2 GB free space, an additional 6.8GB space will be taken for some overhead, resulting in 122.4GB usable space? So the question is, since the entire HD is already formatted, what is this 6.8GB used for?

---

### Post by jadtech on 2012-04-13
yupp that is a fact its only estimated 134.6 from the start 

129.2 is free how ever its will only allow you to use 122.4

it may well be able to defrag the space and  still change things too

---

### Post by chenxinghao on 2012-04-13
I see. Thank you for the patience.

---

