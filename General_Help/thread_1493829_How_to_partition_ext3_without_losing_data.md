---
title: "How to partition ext3 without losing data?"
date: 2010-05-26
forum: General Help
---

### Post by darijan on 2010-05-26
**because what i was looking for was complicated, i am going to edit post**

[COLOR="Red"][B][I]I have laptop with ubuntu on it. I have one ext3 partition with ~220GB.

I want to delete ubuntu and create two ntfs partitions (50+170GB) so i can install windows 7  later.

how to do that using GParted Live CD?[/I][/B][/COLOR]

---

### Post by dino99 on 2010-05-26
how to set your partitions

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

boot on partedmagic to resize, format your disk/partitions (never on active disk)

---

### Post by darijan on 2010-05-26
that is not good for me :(
i have to partition my hdd WITHOUT losing data on it...

---

### Post by oldfred on 2010-05-26
You have to run partitioning software from a liveCD, so partitions are not mounted. Often liveCDs see your swap partition and mount it to speed up the liveCD but then for partitioning you have to click on the swap partition and swapoff.

---

### Post by darijan on 2010-05-26
**because what i was looking for was complicated, i am going to edit post**

[COLOR="Red"][B][I]I have laptop with ubuntu on it. I have one ext3 partition with ~220GB.

I want to delete ubuntu and create two ntfs partitions (50+170GB) so i can install windows 7  later.

how to do that using GParted Live CD?[/I][/B][/COLOR]

---

### Post by oldfred on 2010-05-26
If you are going to install windows make sure that partition is a primary partition.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Serpher on 2010-05-26
You can't. Because you're putting a different filesystem on it it's going to be pretty much impossible to retrieve any data, with is difficult and not usually done unless there was an accident anyway. Also you can only make a **proper** NTFS partition using the Windows CD you'll be getting.

---

