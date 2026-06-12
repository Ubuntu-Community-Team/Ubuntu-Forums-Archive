---
title: "Give ubuntu more disk space?"
date: 2011-01-31
forum: General Help
---

### Post by loganbell45 on 2011-01-31
Hi, i have fallen in love with linux - but for practical reasons need to keep windows, i'd like to give linux more disk space so i can install more programs etc. but i have no idea how to go about doing this, i tried using the live cd to redo the partitions and was able to make the windows part smaller but that's all i could do... here's a picture of the partitions. Any ideas?):P[IMG]http://www2.picturepush.com/photo/a/4970055/img/4970055.png[/IMG]

---

### Post by drs305 on 2011-01-31
You would need to unmount all partitions, back up important data, and then:

1. Shrink sda1
2. Move sda2 to the left
3. Expand sda3 to the left
4. Expand sda5 to the left

Since you are moving the partitions to the left this is going to take a long time to accomplish (each of the larger tasks could take more than an hour). I'd recommend accomplishing the Windows partition shrinking (sda1) with Windows software designed for that purpose. You can use linux's Gparted for the other partitions if desired.

I wrote a guide about how to do this:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

At the bottom of that page is another guide that I recommend by *srs5694*

---

### Post by vanadium on 2011-01-31
What is this small sda2 partition? Perhaps, you can simply delete that to already gain space. Then you'd make sda1 smaller.

If sda2 is there to stay, you will need to reduce sda1 first, then move sda2 to the left.

Then you will first need to adjust the extended partition sda3: the cyan blue line. You will need to move the left side. Then, you can move sda5 to the left (will take a while), after which you can enlarge it on the right.

Do this all step by step. After one single change, use the "Apply" button to write the changes to disk. Proceed this way step by step. Resizing a partition is a fast process. Moving a partition, however, will take time.

---

### Post by loganbell45 on 2011-02-01
Thank you both - i've successfully given ubuntu 65GB more space to utilise ;)

---

