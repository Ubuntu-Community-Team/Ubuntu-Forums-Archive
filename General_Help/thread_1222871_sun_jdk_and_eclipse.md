---
title: "sun jdk and eclipse"
date: 2009-07-25
forum: General Help
---

### Post by balan3 on 2009-07-25
hi

This is  my first day with ubuntu and i was wondering if anyone could guide me with installing sun jdk on my ubuntu 9.04 and as well as eclipse. My other question is how much space do i need to install this. I tried using the command apt-get install sun-java6-jdk on root. it starts installing and then there is error. i am not sure what it is? But i think there is less disk space. How do i solve this or even how do i find out how much space is left. I am a complete newbie. I am not sure if the package got completely installed.I would appreciate any help Thanks:(

---

### Post by michy99 on 2009-07-25
First, to find out if there is a disk space problem, run this command in a terminal and post the output:```
df -h
```I am not sure what you mean when you say you ran apt-get install sun-java6-jdk "as root" Do you mean you used sudo?

---

### Post by balan3 on 2009-07-25
Yes i used sudo.This is what i got when i run df -h


               Size    Used   Avail
dev/ sda   2.3G   2.3G     0
tmpfs        1.5G   0        1.5G
Varrun      1.5G   104K
Varlock     1.5G   0
Vdev         1.5G   0
TMPFS      1.5G 508K

---

### Post by balan3 on 2009-07-25
hello again thanks for your reply  i was running windows on one of my partions and now i logged into windows and shrunk the size of the partion and now i have 40 gb of unallocated space left. Now how do i get my Ubuntu to use this space?I am sorry but i am still learning to use this forum so pls be patient with me if i make mistakes

---

### Post by michy99 on 2009-07-25
You definitely need to expand your ubuntu partition. 2.3 gigs isn't enough. Here's a good guide on how to do it:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by balan3 on 2009-07-26
hey thanks a lot! This link looks very useful and it will help a lot. I will try this out and see if i can continue with my installation. :)

---

