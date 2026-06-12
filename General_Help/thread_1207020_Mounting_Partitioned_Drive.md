---
title: "Mounting Partitioned Drive"
date: 2009-07-07
forum: General Help
---

### Post by K_REY_C on 2009-07-07
Somehow lost access to mount one of the drives I've partitioned out for media. It simply fails to mount (but I can see it) and won't open. Any help appreciated. Thanks. K_REY_C

---

### Post by michy99 on 2009-07-07
What is the output of```
sudo fdisk -l
```

---

### Post by K_REY_C on 2009-07-07
Sorry, not sure how to copy and paste from/in terminal. Image of output is here: [Output]("http://i291.photobucket.com/albums/ll297/K_REY_C/Screenshot.png")

I have two external drives attached and number of partitions - there is one partition (about 95 GB) that I can't open anymore. 

Thanks for the help! KYLE

---

### Post by K_REY_C on 2009-07-07
Sorry for the confusion. The word "Output" above is a link to the output. Any help still appreciated. Thanks very much! KYLE

---

### Post by K_REY_C on 2009-07-09
Haven't heard anything about getting the partition to mount. Haven't been able to find the answer myself. Any and all help appreciated. 

KYLE

---

### Post by merlinus on 2009-07-09
Which partition are you trying to mount?  Is there an entry for it in /etc/fstab?

---

### Post by K_REY_C on 2009-07-13
I'm trying to mount /dev/sda3

I don't see it in /etc/fstab

How would I fix this? What would I add?

Thanks very much.

---

### Post by K_REY_C on 2009-07-13
> **merlinus said:**
> Which partition are you trying to mount?  Is there an entry for it in /etc/fstab?

Thanks for directing me to fstab. This solved my problem. A little research later and I added the following line to /etc/fstab :

/dev/sda3 /media/TEN vfat defaults,user,auto 0 0

All problems solved. 

Thanks very much!

---

### Post by merlinus on 2009-07-13
Excellent!  And good on you for taking the time to do some research and figure it out!!

---

