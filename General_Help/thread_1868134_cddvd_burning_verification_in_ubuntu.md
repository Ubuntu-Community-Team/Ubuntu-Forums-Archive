---
title: "cd/dvd burning verification in ubuntu"
date: 2011-10-23
forum: General Help
---

### Post by 123456789123456789123456 on 2011-10-23
This is just a general question, I have recently had issues with some disks I burned using the default burning software that comes with 11.10.  I was wondering if there is a program for ubuntu 11.10 that verifies the burned cd or dvd to make sure there is no issues with integrity like image burn does on the pc.

---

### Post by micael3000 on 2011-10-23
Hello and Yes,

Try k3b, it is available on Ubuntu Software Center and it is really much more complete than Brasero.

[]'s.

---

### Post by oldtimer7777 on 2011-10-23
> **micael3000 said:**
> Hello and Yes,

Try k3b, it is available on Ubuntu Software Center and it is really much more complete than Brasero.

[]'s.

Yes K3B has disc checking and verification. But if you have a new writer you shouldn't have to worry too much about that these days.

---

### Post by crazy bird on 2011-10-24
> **123456789123456789123456 said:**
> This is just a general question, I have recently had issues with some disks I burned using the default burning software that comes with 11.10. I was wondering if there is a program for ubuntu 11.10 that verifies the burned cd or dvd to make sure there is no issues with integrity like image burn does on the pc.
 
Just check synaptic for it. There are some solutions which can be found in synaptic.

---

### Post by veggen on 2011-10-24
You can check integrity in Brasero as well. Tools->Check integrity. But it is much better if you created MD5 digest of the original data (before it was burnt) and then used the mentioned option to check against that.
There's also a dedicated tool that can be used separately and has a gazillion useful options, but I can't remember it's name for the life of me...

---

