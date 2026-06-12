---
title: "error: too small lower memory after HDD fills up"
date: 2012-01-25
forum: General Help
---

### Post by ChemMeister on 2012-01-25
Hello,

I was running an expensive calculation that my guess generate very large dump files that filled up my 120 GB partition, i got a message from Ubuntu saying disk memory is low, and then the computer got really slow so i decided to restart, however since then, i cant get to Ubuntu as the system hangs after i chose Ubuntu. Also when I run a memory test i get the error too small lower memory (0x99100>0x94400). When I booted from live CD, i saw that I only have left 1GB of disk space. 
Any ideas how to fix this problem, my first thought was to locate the large dump files and delete them, but i was not allowed to do that, besides i am not even sure if that will solve the problem. Thanks in advance.

---

### Post by Tony Flury on 2012-01-25
You could try to boot with the Live CD - mount the HD and then go look for the big files.

My guess is that the big dump files may well cause some "issues".

---

### Post by oldos2er on 2012-01-25
There is some info here on freeing up hard disk space: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

This may explain the memtest error: [https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839](https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839)

---

### Post by ChemMeister on 2012-01-25
Thanks for the responses. My main problem is that i can view the files on the partition from live CD but I cannot delete any because of folder permissions that i cannot change. Can you change the permissions?

---

### Post by oldos2er on 2012-01-25
Don't change permissions on partitions, instead give yourself admin privileges: ```
gksudo nautilus
```

---

