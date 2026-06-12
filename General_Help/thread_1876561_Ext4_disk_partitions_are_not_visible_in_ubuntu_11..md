---
title: "Ext4 disk partitions are not visible in ubuntu 11.10"
date: 2011-11-06
forum: General Help
---

### Post by apocalyptod on 2011-11-06
Im a new user of linux environment. I just have installed  Ubuntu 11.10 in my system and Im unable to see the disk partition in  which I have installed the OS. Size of the main disk is 100 GB and I  want to see it back so that I can save my data in it. The  disk format is ext4 and the mount point was "/". Can you help me to get mount this partition?


  Thanks and regards.

---

### Post by Mark Phelps on 2011-11-06
How did you install Ubuntu? Was it inside Windows using wubi?

If so, you most probably installed it inside your Windows main parition. That is mounted under /host.  If you go there, you will see the remainder of that partition.

---

### Post by apocalyptod on 2011-11-06
No, I have completely removed my Windows files. I have created two new partitions from my previous disk in which I had installed Windows. One of them has a mountpoint "/" and another one is "/home". But both of them are not visible while rest of the NTFS disk drives are quite visible and working good. Any idea what's going on?

PS: Im a noob when we talk about Ubuntu or Linux. So please, take care of it when you answer to my problems. :)

---

### Post by Truefire on 2011-11-06
"/" and "home" are more like virtual partitions, unless you set them up otherwise. It's not the equivalent of "C" "F" and whatever else.

The main drive that home is on, your main folder, is the drive you want to use.

---

### Post by mcduck on 2011-11-06
What makes you think you can't see those partitions?

If you weren't able to see and access them you wouldn't even be abe to use your Ubuntu system. The partition mounted as / is your system partition, so obviously you are using it all the time. And same goes for the /home partition, that's where your home is located in so every file you save in your home direcory goes to that partition...

Perhaps you are just confused by the way how Linux shows all your partitions as parts of the one and the same file system hierarchy iinstead of having multiple hierarchies and drive lettrs etc. iike Windows does?

---

### Post by Rubi1200 on 2011-11-07
Please post the results of the boot info script.

There is a link at the bottom of my post with instructions.

---

### Post by coffeecat on 2011-11-07
@apocalyptod, you have tagged your thread "Lubuntu", yet you refer to Ubuntu in your posts. Please confirm which you are using and a staff member can change the tag for you if necessary.

---

