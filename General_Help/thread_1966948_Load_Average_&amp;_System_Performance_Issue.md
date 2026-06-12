---
title: "Load Average &amp; System Performance Issue"
date: 2012-04-27
forum: General Help
---

### Post by Xanko on 2012-04-27
Just updated to 12.04, and now it seems that the computer is always running at .75 - 1.0 load average (and this is just idling with a window open for IOTOP and HTOP). I would expect the load to be around .1 - .2 (this is a dual core system)

htop is showing IOTOP and compiz as the main program using CPU time though they have used very little CPU time overall, also IOTOP has been idle for most of the day with the exception of kjournald.....

any ideas on how to troubleshoot this further? Perhaps the processors are not changing frequency to speed up for higher demand?

---

### Post by faucon50 on 2012-05-06
It's a kernel bug:

[https://bugs.launchpad.net/ubuntu/+sour](https://bugs.launchpad.net/ubuntu/+sour) … bug/985661

---

### Post by Doug S on 2012-05-06
See also: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811) 
 
and the above link was odd, reposting: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661)

---

