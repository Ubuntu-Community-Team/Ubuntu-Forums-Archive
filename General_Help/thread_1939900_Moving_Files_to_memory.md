---
title: "Moving Files to memory"
date: 2012-03-12
forum: General Help
---

### Post by Ceiber Boy on 2012-03-12
is it possible to 'store' files in memory? Hear me out!

I have a shed of memory and a slow HDD, so when transcoding large files, instead of trying to read and write to the HDD at the same time would it be quicker to move all the data to memory? I could then use my quad core CPU flat out. Avoiding the bottleneck of my HDD.

i am expecting one of three answers:
1, no, stop being silly.
2, yes but the specific program your using would have to be writtern to do so.
3, yes, this is how

Thanks.:p

---

### Post by Dave_L on 2012-03-12
You can easily create a RAM disk.

Example of creating a 512mb RAM disk with mount point /tmp/ram:

```
mkdir -p /tmp/ram
sudo mount -t tmpfs -o size=512M tmpfs /tmp/ram/
```

---

### Post by Ceiber Boy on 2012-03-13
> **Dave_L said:**
> You can easily create a RAM disk.

Example of creating a 512mb RAM disk with mount point /tmp/ram:

```
mkdir -p /tmp/ram
sudo mount -t tmpfs -o size=512M tmpfs /tmp/ram/
```


Brilliant. Thanks you Dave

---

### Post by Bucky Ball on 2012-03-13
Ceiber Boy and others please take note; from the heading of this page:

> The Community Chat area is for lighthearted and enjoyable discussions, like you might find around a water cooler at work.

This forum is not intended for problem-solving. Please use appropriate forums in future. Thanks. ;)

---

### Post by coffeecat on 2012-03-13
Support thread. Not a Cafe topic.

*Thread moved to **General Help**.*

---

