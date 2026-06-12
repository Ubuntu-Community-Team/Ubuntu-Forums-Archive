---
title: "how can i find how much i have downloaded in the past days? it is important"
date: 2009-07-24
forum: General Help
---

### Post by chriskin on 2009-07-24
i need to know how much i have downloaded in the past days because i use someone elses 3g internet and don't want to charge him by downloading more than comes with the monthly payment.

---

### Post by TeoBigusGeekus on 2009-07-24
Perhaps the site of your isp could help you - they log everything.

---

### Post by chriskin on 2009-07-24
> **TeoBigusGeekus said:**
> Perhaps the site of your isp could help you - they log everything.


it is not my connection but a friend's that got it from work.
so i can't use that

doesn't my system log my downloads somewhere?

---

### Post by LowSky on 2009-07-24
if its verizon (only one I've ever used and know anything about) their website tracks and log everything, but you need his account knowelge to see it.

---

### Post by LowSky on 2009-07-24
> **chriskin said:**
> it is not my connection but a friend's that got it from work.
so i can't use that

doesn't my system log my downloads somewhere?

you can use the network manager to see how much traffic you used while the PC has been on, but not days past... sorry

Note most Air cards have a 5GB download limit, so unless you have been downloading ISO's and Streaming Audio and video non stop you will be fine

---

### Post by chriskin on 2009-07-24
its vodafone, but i have no knowledge of the passwords etc

---

### Post by chriskin on 2009-07-24
> **LowSky said:**
> you can use the network manager to see how much traffic you used while the PC has been on, but not days past... sorry

Note most Air cards have a 5GB download limit, so unless you have been downloading ISO's and Streaming Audio and video non stop you will be fine
  
i hope i'm not off limit yet
i will stop most network activity if possible, unless i find a way to check it


it's just that the charges after the initial amount are TOO much, something like 3 cents for every KB. (3 euros per mb , 3000 euros per gb , a small car for a multi-gb game (!!!) )

---

### Post by Cheesemill on 2009-07-24
You can get software that will keep track of your internet usage, but only after you install them.

---

### Post by philcamlin on 2009-07-24
> **Cheesemill said:**
> You can get software that will keep track of your internet usage, but only after you install them.

+1 you cant see what you did befiore if you didnt log it :D

---

### Post by Cheesemill on 2009-07-24
> **chriskin said:**
> it's just that the charges after the initial amount are TOO much, something like 3 cents for every KB. (3 euros per mb , 3000 euros per gb , a small car for a multi-gb game (!!!) )
 
If it's 3 cents every KB then it's actually 30 euros per MB, 30000 euros per GB, etc...

---

### Post by ajgreeny on 2009-07-24
Install *vnstat* and then for the days after installation just run ```
vnstat -d
```and you will get output like this, but only for days after the install.  For days prior to that you may have to estimate it somehow.
```
eth0  /  daily

    day         rx      |     tx      |  total
------------------------+-------------+----------------------------------------
   17.07.     43.23 MB  |    1.92 MB  |   45.15 MB   %
   18.07.     26.92 MB  |    2.92 MB  |   29.84 MB
   19.07.    188.28 MB  |    8.31 MB  |  196.59 MB   %%%%
```

---

