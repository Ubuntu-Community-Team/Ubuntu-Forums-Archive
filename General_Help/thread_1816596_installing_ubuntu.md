---
title: "installing ubuntu"
date: 2011-08-02
forum: General Help
---

### Post by sandeepkumarh67 on 2011-08-02
Hi

I am running ubuntu and windows 7 (dual boot mode).
Now I want to remove windows and keep ubuntu only
I have 500 gb hardisk with 4 partitions. windows and ubuntu are installed in first partition i.e. :C and my other data (files music) etc. in other 3 partitions (:D,:E and :F)
I want to know if I install ubuntu will i loose all the data of my hard disk or only that on drive :C as happens during installation of windows? :confused:
I read many posts but am still unclear

thanks 
sandeep

---

### Post by axatrikx on 2011-08-02
You will not lose data on the other drives if u follow the set up details carefully. During ubuntu installation, it will ask whether to install it as a whole(which would remove data) or on specific partition of your choice. Opt the manual or advance partition option and chose C drive. 
check this post for more info
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Topsiho on 2011-08-02
Your post is very unclear to me.

How can you have Windows and Ubuntu installed into one partition, C: (and not :C), which probably means that Windows is installed in /dev/sda1, in Linux speak. Then you say that your data are put into D:, E:, and F:, which would probably mean /dev/sda2, /dev/sda3 and /dev/sda4. That makes a total of 4 partitions. And where is Ubuntu?

If you plan to install Ubuntu some place you need 2 or 3 extra partitions. As you can have only 4 primary partitions on a disk, you need some planning to do, and replace one primary partition with an extended partition, into which you can place any number of logical partitions, numbered /dev/sda5, /dev/sda6, and up.

So the best thing to do is that you begin with putting data in F: and possibly E: into D:, to begin with, in order to free enough space for an extended partition, in which to install Ubuntu.

If I am correct in my assumptions, of course. And if not, you can adapt this to the real situation.

The partitions of Ubuntu must be for / and swap, or better: for /, /home and swap, each in it's own partition.

And of course the best advise I can, and should, give is: before you start, back up anything you don't want to lose ...

Topsiho

---

### Post by sandeepkumarh67 on 2011-08-02
Thanks for such a quick reply

thanks axatrikx for helpful link. i think it will solve my problem.

@ Topsiho i would like to show my problem to you by this picture iam attaching. hope this clears my point.

waiting for ur reply

thanks 
sandeep

---

### Post by Topsiho on 2011-08-02
OK, you don't have a dual boot, but Ubuntu is installed within Windows, with Wubi.

I don't have experience with Wubi.

You say you want to keep Ubuntu, and remove Windows.

From your setup I see that you have a partition with Windows, and three data partitions. I guess they are all on one disk.

The data partitions you want to keep, and the Windows partition (the partitions on which Windows is installed), which is C:, or in Linux speak /dev/sda1, may be blown into oblivion (may be wiped).

And that I think you should do. And on it install Ubuntu, a real install, from a liveCD.

You could do this when installing, but I prefer to prepare this first, before installing. A greater ease of mind, as you do one thing at a time, I guess.

1. Study first the situation presented in Windows, which you showed in the first screenshot. Make notes of what you see there.
2. From the live CD you start GParted, and study very well the situation presented, making notes of what you see. Compare this to point 1.

This is to be able to identify without any hesitation the partition on which Windows is installed, and which are te data partitions.

When you are really certain, then you can wipe the partition on which Windows is installed. This is almost certainly /dev/sda1. This gives you nearly 100 GB of unallocated space.
In this you create 2 or 3 LOGICAL partitions. I prefer 3:

1. a LOGICAL partition for /       (root). Say 10, or even 15 GB.
2. a LOGICAL partition for /home   (for your personal files)
3. a LOGICAL partition for swap    (twice your working memory)

The size of the /home partition you have to determine from available unallocated space, - (/ + swap).

The filesystems to choose: for / and /home I always use ext4. For swap you use ... swap :)

The actual mounting of the partitions to /, /home and swap is done during the install.

And of course you have to read the link to psychocats, given by axatrikx :)

Hope this helps, it's not difficult, but you need to be careful and attentive. You have to be careful NOT to format any partition with data, probably /dev/sda2, /dev/sda3 and /dev/sda4. If you format those, your data are lost, and that's not what you want.

Topsiho

---

### Post by sandeepkumarh67 on 2011-08-02
wow! you have resolved my query and removed my fear, Topsiho. I will be careful during installation though, as you have said.
Thankyou very much dear
sandeep

---

### Post by dino99 on 2011-08-02
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Topsiho on 2011-08-02
sandeepkumarh67, you are welcome :).

Topsiho

---

