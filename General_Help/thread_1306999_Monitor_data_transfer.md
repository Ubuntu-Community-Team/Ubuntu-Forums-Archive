---
title: "Monitor data transfer"
date: 2009-10-30
forum: General Help
---

### Post by kotch on 2009-10-30
Hi,

basicly I have a few different partitions on a drive which users can upload/download to.

I thought that if I could monitor the total amount of data transfered for each of these partitions i could monitor bandwidth usage.

Does anyone know of any tools that can do this for me,

Thanks

---

### Post by shaggy999 on 2009-10-30
I need a little more clarity on what exactly you want. How fine grained does this have to be and are you referring to network or disk throughput? If all you want is to know how much bandwidth is used by a network connection look into 'vnstat'.

---

### Post by kotch on 2009-10-31
well i wish to monitor the network traffic used by each user but the easiest way that i can think of with the setup i have got is to measure disk throughput on each users partition.

It doesn't have to be massively accurate but within 5% would be good.

I have looked at 'vnstat', but from the look of things it can only monitor traffic for the whole network not individual users.

---

### Post by shaggy999 on 2009-10-31
I don't see how disk throughput has any correlation to network throughput.

I think you want to look into pmacct - [http://www.pmacct.net/](http://www.pmacct.net/)

It's in the repos:

sudo apt-get install pmacct

---

### Post by shaggy999 on 2009-10-31
This may also help:

[http://www.linux.com/archive/articles/50649](http://www.linux.com/archive/articles/50649)

---

### Post by kotch on 2009-11-01
> **shaggy999 said:**
> I don't see how disk throughput has any correlation to network throughput.

In a normal situation there wouldn't be but since the partitions are only used for files which the user uploads/downloads i would think that the disk throughput would be the same as the network throughput for that individual user and their partition.

To make it clear I am wishing to monitor the total disk throughput over a months for multiple separate partitions.

---

### Post by shaggy999 on 2009-11-01
> **kotch said:**
> In a normal situation there wouldn't be but since the partitions are only used for files which the user uploads/downloads i would think that the disk throughput would be the same as the network throughput for that individual user and their partition.

To make it clear I am wishing to monitor the total disk throughput over a months for multiple separate partitions.

I'm not so sure on that. Linux caches files very aggressively and will use all the available extra ram it has. So a file could get written to the hard drive and then downloaded by someone else, but most if not all of that file could be sitting in memory which results in no access on  your hard drive. In addition, network transfers involve re-sending packets quite often and the header parts of packets account for part of your bandwidth. Over time that adds up.

---

