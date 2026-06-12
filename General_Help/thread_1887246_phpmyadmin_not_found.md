---
title: "phpmyadmin not found"
date: 2011-11-26
forum: General Help
---

### Post by eltiti55555 on 2011-11-26
I installed LAMP and phpmyadmin following this video [http://www.youtube.com/watch?v=-mG8kgMHK2A]("http://www.youtube.com/watch?v=-mG8kgMHK2A") and I can get every single step working but the last, in which I need to connect to phpmyadmin through a browser. I have two virtual clients running, one is Ubuntu desktop and the other one is Ubuntu server. On the server I installed LAMP and phpmyadmin,and from the desktop I try to reach the phpmyadmin using Firefox. As you can see I get this error [http://postimage.org/image/9ib06w27b/]("http://postimage.org/image/9ib06w27b/") Any thoughts?

---

### Post by eltiti55555 on 2011-11-26
Bump!

---

### Post by eltiti55555 on 2011-11-26
So... no one bothers even to look...?

---

### Post by lisati on 2011-11-26
Please don't "bump" too often: the rule-of-thumb on this forum is once every 24 hours.

I don't actually use phpmyadmin but it looks to me like a link didn't get put in the place it should be.

---

### Post by azmyth on 2011-11-26
Which virtual sw are you using? For example, Virtual Box. The default for VB at least is to setup the guest host to be using NAT which doesn't assign an IP thus you won't be able to access from one virtual machine to another. I believe you need to setup the internet to use the bridge adapter in each guest host so it will assign an ip to each guest.

---

### Post by c.cobb on 2011-11-26
There are probably good reasons for using phpmyadmin. 

OTOH, you might want to try some better tools. [Here are some that I like]("http://ubuntuforums.org/showthread.php?t=1877871#post11439616") with examples of flexible usage.

---

