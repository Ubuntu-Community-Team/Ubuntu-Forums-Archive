---
title: "Grub rescue"
date: 2009-12-25
forum: General Help
---

### Post by lost-star on 2009-12-25
Hey people,

I am a windows/apple(mac) user. Currently I am trying to install ubuntu on my windows computer. But after I installed it I got this from start.

error: no such disk
grub rescue>

and well that's all. I have been going trough sites to see how I can solve this and get things running since well I can't do anything else.

---

### Post by lost-star on 2009-12-25
tried ls, got 3 partitions called

(hd0) (hd0,1) (fd0)

tried to setroot=

and than fallow the things as said in the list. But every time I get error="no such disk"

---

### Post by garvinrick4 on 2009-12-25
Open program gparted and see what it says, it shoud say sda1 system, sda2 OS  then
a partition that says extended  and the linux and swap inside the extended partition.

I am sorry you cannot open anything can you. Here are some good reads to try to get
you going.
  	 	 	 	 	 	  [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
 

 

 [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
 

 

 [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 

 [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

