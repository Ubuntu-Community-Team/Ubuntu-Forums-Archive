---
title: "noobie couple questions"
date: 2010-05-26
forum: General Help
---

### Post by choochoousmc on 2010-05-26
got 10.04 lts working. But I had it install on the whole hard drive as a trial.
Now can I shrink the partition.
I need two others  1 go gig for windows, one 100 gig for AL DATA
how do I do this , please provide all commands I may need to type in manually.
should I format windows FAT 32 or NTFS?
What format should I use for the DATA partition so Ubuntu and Windows can access it.

How can I become the permanent administrator that let's me edit the /rpool.

More questions????????

---

### Post by Serpher on 2010-05-26
Boot from a live CD (Because your Ubuntu partition can't be mounted), and go to System --> Administrator --> gParted

After this right click your EXT4 partition, shrink it, then when you install Windows use that to make 2 NTFS partitions.

---

### Post by choochoousmc on 2010-05-27
Ok thanks for that info.
But I am NOT planning on windows soon.
First I want to play with unbuntu.
I still need the two extra partitions though.
Can't I do it from Gpartd?

Does Ubuntu natively support NTFS for reading and writing?

I have a lot of pictures and music files on an external hard drive that is formatted in NTFS.
Some I want to transfer to the notebooks hard drive, that's why I want to know.

Once the partitions are done then I will be playing with the system!



QUOTE=Serpher;9366217]Boot from a live CD (Because your Ubuntu partition can't be mounted), and go to System --> Administrator --> gParted

After this right click your EXT4 partition, shrink it, then when you install Windows use that to make 2 NTFS partitions.[/QUOTE]

---

### Post by Darkness Des on 2010-05-27
According to some, Ubuntu is TERRIBLY incompatible with NTFS. In my 2 years of using it, this was never the case. I have a second internal hard drive that's 90% NTFS and it works wonderfully. I also have an external drive that is 100% NTFS and I've never had a single issue with it. So you should be fine.

GParted can also be used for making partitions. That's what it is mostly used for.

---

### Post by towheedm on 2010-05-27
When I switched to Ubuntu from Windows last December I kept my old 80gigs HD which has 5 NTFS partitions.  One of these is my data partition.  I has not had any problems so far transferring files between any NFS partitions and my ext4 home partition.  Ensure you use the [COLOR=Red]ntfs-3g[/COLOR] package.

Installing the [COLOR=Red]ntfsprogs[/COLOR] package will also allow you to grow and shrink (among other things) your NTFS partitions.

If you plan on using Windows NT or above, you should definitely make these partitions NTFS.

---

### Post by choochoousmc on 2010-05-28
An update here. Thanks to those that responded.
I did as described. I booted from the live CD.
Used Gpartd (which I have used before). Shrunk the one main partition.
Then created two new ones both in NTFS.
What is basic difference between EXT2, 3, 4 as compared to FAT16,32,NTFS,
And in Ubuntu which would be most preferred (future knowledge).
As soon as I rebooted ubuntu recognized both new partitions!!!
Connected to my wireless.

Now need to confirm sound and print is working.  If so I am good to go til I hit a snag, if I do.

Again thanks for help.
using a two month old  Acer Aspire 5532    so far installation has been easy, once I had a good live cd!

---

### Post by dnguyen1963 on 2010-05-28
> **choochoousmc said:**
> An update here. Thanks to those that responded.
I did as described. I booted from the live CD.
Used Gpartd (which I have used before). Shrunk the one main partition.
Then created two new ones both in NTFS.
What is basic difference between EXT2, 3, 4 as compared to FAT16,32,NTFS,
And in Ubuntu which would be most preferred (future knowledge).
As soon as I rebooted ubuntu recognized both new partitions!!!
Connected to my wireless.

Now need to confirm sound and print is working.  If so I am good to go til I hit a snag, if I do.

Again thanks for help.
using a two month old  Acer Aspire 5532    so far installation has been easy, once I had a good live cd!

Boys...I wish you had not removed your Windows OS.  Generally, it is best to defrag the HS in Windows then install Ubuntu.  Ubuntu has a very good installer.  It can install side-by-side with Windows without any problem.  On the other hand, if you have Ubuntu on your HD and you try to install Windows on the same HD, you are going to run into trouble.  Windows does not know how to handle another OS on the same HD.  You might have to re-install Ubuntu after Windows.  Then again, you will probably not miss Windows at all.

p.s. check out the thread about "Ubuntu Freezes" in this forum.  10.04 LTS has a lot of problems with Suspend/Hibernation.

---

### Post by choochoousmc on 2010-06-20
well First I tried Solaris and Open Solaris on the notebook. Well as usual something went wrong. Wiped my whole hard drive. I do have a set of windows seven install disks though
However, after playing with Ubuntu a little I don't think I will install windows. I think I will delete the windows partition and absorb it into another or maybe just rename it.
I have not manually selected suspend / hibernation yet. I just select lock screen. Haven't had a problem yet

---

