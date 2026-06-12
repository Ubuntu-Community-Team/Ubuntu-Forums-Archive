---
title: "Force system to use swap?"
date: 2011-07-06
forum: General Help
---

### Post by adeee on 2011-07-06
yes guys is there any way to force the system to use swap space instead of RAM?
I just upgrade form 512 to 1 gb. and when i installed ubuntu i give the swap space 1gb according to 512mb RAm requirement. now i have 1 gb.
When i use heavy applications i-e firefox, office, any game etc at a time the processing go to 100% and the RAM use 50+% of the memory. no swap memory will be use. so any way to use swap instead of RAM?

---

### Post by dFlyer on 2011-07-06
Let the OS manage the memory and swap. It does it much better than windows any day. Why force it to use the swap which is much slower than RAM.

---

### Post by CatKiller on 2011-07-06
If you aren't running out of RAM all the time you don't have anything to worry about. Why would you want your fast RAM to be left empty while the (several orders of magnitude) slower hard drive gets used instead?

---

### Post by SeijiSensei on 2011-07-06
I agree with the other posters that you should let Linux manage memory and swap.  However you could play with the "[swappiness]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")" parameter and see if it makes a difference.

---

### Post by CatKiller on 2011-07-06
It's not just that you should let Linux manage the memory (which is certainly true), it's that using swap when you don't have to is positively bad. It's so much slower than RAM that never ever using swap should be the goal. I really don't understand why the OP would want worse performance.

---

### Post by SeijiSensei on 2011-07-06
I agree entirely, but since the OP wanted to futz with swappiness, I thought I'd point him in the right direction.

Often the kernel moves some of its relatively-unused parts into swap even when there's memory galore.  Right now my 4GB machine has 10M of swap in use.  They are all kernel items like ksoftirqd.

---

### Post by lakosshoots on 2011-07-06
I believe that the point of the original post is to improve performance. However, as mentioned from the posters above, swap is raw place in HDD which a lot slower than RAM. The idea of swap is to dump RAM and to receover it when the amount of existing RAM is low. 

If you use different applications from time to time, droping cache might help.

sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"

My suggestions is to try another graphical interface, like xfce. It works great on older machines. You can either install it from synaptic, find the package and apply (it will include dependencies) or type

sudo apt-get install xubuntu-desktop

If you need more info about memory management, give it a look.

[http://just-more-thoughts.blogspot.com/2011/06/ubuntu-1104-memory-management-36.html]("http://just-more-thoughts.blogspot.com/2011/06/ubuntu-1104-memory-management-36.html")

---

