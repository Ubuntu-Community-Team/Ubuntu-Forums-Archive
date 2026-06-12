---
title: "Normal user can't write to EXT4 Partition"
date: 2010-03-16
forum: General Help
---

### Post by uylug on 2010-03-16
I have a problem with my recent ubuntu installation.

I bought a 1TB hard disk, split it into three partitions, one for /, the other one for my home folder and the other one for the data that I am going to store. I don't keep everything on my partition specially because i want some data to be independent of the user.

I set my 850 GB partition to mount on /mnt/mydata, however it refuses to write data unless run as root.

I'd like to have read and write access to this with normal users. How can I do this?

Thanks in advance.

---

### Post by amac777 on 2010-03-16
You could give all users full access to that directory using this commend:

```
sudo chmod 777 /mnt/mydata
```

---

### Post by uylug on 2010-03-16
> **amac777 said:**
> You could give all users full access to that directory using this commend:

```
sudo chmod 777 /mnt/mydata
```

OMG.

I NEVER thought chmodding it would do the trick.

Thanks for such a quick reply! ;)

---

### Post by tahitiwibble on 2010-05-20
Hi guys, I have a similar problem and when I use the terminal command I get a "No such file or directory" error.

Can someone help me with a quick fix. Many thanks.


*edit* :)

---

### Post by tahitiwibble on 2010-05-20
I spoke too soon, try as I may I can't write to a second and third internal HD.

Thanks if you can get me out of a fix.

---

