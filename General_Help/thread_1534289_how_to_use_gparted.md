---
title: "how to use gparted"
date: 2010-07-19
forum: General Help
---

### Post by gwvenus on 2010-07-19
Hi Everyone,
I've read everything on Google but I can't find the answer. I've put together a new computer. It has a 500g hard drive. I've installed windows but I want to have it dual boot to linux. I only want to use 80g for linux so I figured I could use gparted. I was able to create my unallocated 80g no problem but I don't know how to to set it up for
the various partitions. There isn't even an option for root! Could you give me a run through and what size each partition should be if you have the time? I'm still pretty much a noobie, so if you could spell it out for me it would be greatly appreciate!
Thanks,
Gary

---

### Post by mike555 on 2010-07-19
If your not too picky just let Ubuntu do it for you ........ but if you want a separate /home then you can do that .... I would set 20gb for / and 2gb for swap ,and the rest for /home.

---

### Post by gwvenus on 2010-07-19
Hi Mike 555,
I appreciate your quick reply but I have no idea how to get past creating the unallocated space. I need a step by step guide how to actually create my new partition. Kind of like do this first and then do this next and so on. I've read every article on google and it's not even covered. 
Thanks Again,
Gary

---

### Post by ST3ALTHPSYCH0 on 2010-07-19
Right click in the unallocated space and choose "new". Let it take the whole amount and select EXT3 or EXT4.
Start the installer, when you get to set up partitions choose "manual"
Check the box in the row for the EXT filesystem marked "use this partiton" 
double chick the cell that says "mount point"
enter "/"
click "next"
You don't need to format if you set it as an EXT in Gparted.

---

### Post by oldfred on 2010-07-19
Some more links:

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)

---

### Post by utnubuuser on 2010-07-20
Plenty of good documentation in the wiki, including partitioning:> [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by gwvenus on 2010-07-20
> **ST3ALTHPSYCH0 said:**
> Right click in the unallocated space and choose "new". Let it take the whole amount and select EXT3 or EXT4.
Start the installer, when you get to set up partitions choose "manual"
Check the box in the row for the EXT filesystem marked "use this partiton" 
double chick the cell that says "mount point"
enter "/"
click "next"
You don't need to format if you set it as an EXT in Gparted.
Hi ST3ALTHPSYCHO,
Thank you for the information. It worked to a point but then I got an error message stating that I have no swap file. Shouldn't I also have a boot and a home file as well?
Could you tell me how to set this up?
Thanks Again,
Gary
Thanks to everyone who answered me question.

---

### Post by oldfred on 2010-07-20
If you are doing manual partitioning you have to plan what partitions you want or need including perhaps some or space for some in the future. I recommend /home and do not recommend a separate /boot unless you have a very old computer with a BIOS that only can read part of a new larger hard drive. 
You should also create a swap but do not need to format it. Swap should be about 2GB unless you have a very large hard drive and/or want to hibernate then it should be slightly large than RAM. Back when RAM was only 256MB swap was supposed to be two times RAM.

The separate /home allows you to upgrade easier with a new clean install and separates operating system partition from your data partition. If you have a separate /home the root partition only needs 10-20GB, swap 2GB and the rest should be /home.

---

