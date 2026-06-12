---
title: "Why is so much space taken up on a newly formatted partition"
date: 2011-05-06
forum: General Help
---

### Post by iconoclast hero on 2011-05-06
I have a 500gb usb drive that I am using as my main HDD since my laptop destroys internal HDDs.  I want to create a separate partition for the home directories ([https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)) and used gparted to make a new partition.  If I look at the partition information it says I'm using 307.85 MiB of the 9.85GiB I partitioned and formatted it to (ext4).  When I go to /media where I have it mounted via fstab, it says that 652.5MB are used...  I am dumbstruck to figure out what is using this space because if I sudo -i and go to /mount/home and execute ll, this is what I get:
```
root@ruth-pc:/media/home# ll
total 8
drwxr-xr-x 2 root root 4096 2011-05-06 13:24 ./
drwxr-xr-x 7 root root 4096 2011-05-06 12:22 ../

```If anyone has some insight, I'd appreciate how to get back b/w .3 and .65gigs on that partition.

Thanks

---

### Post by Keypel on 2011-05-06
This might not be relevant to your thread but for starters you get scammed the moment you purchase any hard drive, memory stick, or flash drive.

For instance, a hdd that is advertised as a 1tb is only 931.32gb. It is a marketing scam that dates back to the days of the 5.25 floppy. Unfortunately all manufactures to this day partake in this scam. Basically manufactures at the time felt 1000 kilo's was close enough to 1024 so they decided it would be ok to round up.

The bigger storage devices get... the more you notice this difference.

---

### Post by compmodder26 on 2011-05-06
Here is a page describing what that space is and how you can reclaim it if you like:

[http://odzangba.wordpress.com/2010/02/20/how-to-free-reserved-space-on-ext4-partitions/](http://odzangba.wordpress.com/2010/02/20/how-to-free-reserved-space-on-ext4-partitions/)

---

### Post by ashmew2 on 2011-05-06
In a nutshell , on ext* partitions , some percentage of space is reserved (by default 5%) in case of emergencies for the superuser if he/she might run out of free space everywhere..You can just tune it down to 0% (of ur /home etc) , You dont really need to touch your root partition (/) though ;D

---

### Post by srs5694 on 2011-05-07
There are three main issues that can result in such confusion:


[list]
[*][b]Units[/ib] -- Disk manufacturers use the International System of Units (SI units) correctly, but many other manufacturers in the computer industry and computer programs have historically abused these units. Relatively new [IEEE-1541](http://en.wikipedia.org/wiki/IEEE_1541-2002) units clarify matters, but are still not universally used. A 500 GB (500 x 10^9 bytes) hard disk is, in IEEE-1541 units, a 465 GiB (465 x 2^30 bytes) disk. This is not, contrary to Keypel's assertion, a scam by the manufacturers (although they may have been happy to conform to the SI standards to make their drives seem bigger to consumers used to the abuse of SI units); the problem is really with the industry as a whole, which misused a well-established system of prefixes that have very precise definitions. I don't think this is the source of your issue, though, iconoclast hero, since this type of confusion would not make a disk utility report that space was actually in use; you'd just see that a 9.85 GB partition was being reported as 9.17 GiB in size. (Most Linux disk utilities today do use the relevant units correctly.) I note also that you used the IEEE-1541 units in some places in your post, so you may already understand this.
[*]As ashmew2 says, the ext2/3/4fs family reserves 5% of its space for use by root. On a 9.85 GiB partition, this amounts to 0.4925 GB (470 MiB). This value is higher than one of the estimates of used space you got, but lower than another, so I suspect it's *part* of what you're seeing. You can adjust this value by using the tune2fs utility, as in "sudo tune2fs -m 0 /dev/sda2" to adjust the reserved space percentage to 0 on /dev/sda2. You should only do this when the filesystem is unmounted.
[*]Filesystems reserve a certain amount of space for their own necessary data structures. The single biggest eater of space on this score is the journal. I don't recall offhand precisely how large the journal is in an ext2/3/4 filesystem, so I'm not sure how much of what you're seeing can be attributed to this cause. Chances are it's at least part of the issue, though. You can find the journal size on any specific ext3/4fs volume by using dumpe2fs, as in 'sudo dumpe2fs /dev/sda2 | grep "Journal size"' to find the size of the journal on /dev/sda2.
[/list]


Of these three issues, only the 5% reserved space is something you can do anything about or should worry about, at least on most partitions. On very small partitions, such as a ~200 MiB /boot partition, the journal space can be enough of an issue that you might want to do without a journal entirely on such partitions. You'd do this by dropping back to ext2fs.

Also, keep in mind that different filesystems allocate space for files in different ways. Thus, if you go "shopping around" and test ext2fs, ext3fs, ext4fs, ReiserFS, JFS, XFS, and Btrfs (all the current Linux-native filesystems), you'll find that some give you more free space to start with than others; but because of allocation efficiency or inefficiency, the one with the most free space at the start might or might not enable you to store more files on it.

---

### Post by iconoclast hero on 2011-05-17
Thanks all...  I think the source of the problem was the 5% reserve space.  I cut it down to 2% and mounted it at /home.  I do think that the disc manufactures have played a bit of a game but at the end of they day they haven't, strictly speaking, done anything illegal.  That said, when my first HDD was a 5.25" 20 MB drive and now I have an external .5 TB drive that is "3.15 in Horiz x 5.12 in Vert in x 0.49 in Depth Weight: 0.35 lbs (0.16 kg)" If it was a scam all along, the customer is still better off for it.

I am confused as to what you mean by my mixing IEEE and SI units.  I think that one utility reported the space one way and another utility reported it a different way...and to be perfectly honest, I didn't know that there was a distinction between IEEE and SI units.

> **srs5694 said:**
> There are three main issues that can result in such confusion:


[LIST]
[*][b]Units[/ib] -- Disk manufacturers use the International System of Units (SI units) correctly, but many other manufacturers in the computer industry and computer programs have historically abused these units. Relatively new [IEEE-1541]("http://en.wikipedia.org/wiki/IEEE_1541-2002") units clarify matters, but are still not universally used. A 500 GB (500 x 10^9 bytes) hard disk is, in IEEE-1541 units, a 465 GiB (465 x 2^30 bytes) disk. This is not, contrary to Keypel's assertion, a scam by the manufacturers (although they may have been happy to conform to the SI standards to make their drives seem bigger to consumers used to the abuse of SI units); the problem is really with the industry as a whole, which misused a well-established system of prefixes that have very precise definitions. I don't think this is the source of your issue, though, iconoclast hero, since this type of confusion would not make a disk utility report that space was actually in use; you'd just see that a 9.85 GB partition was being reported as 9.17 GiB in size. (Most Linux disk utilities today do use the relevant units correctly.) I note also that you used the IEEE-1541 units in some places in your post, so you may already understand this.
[*]As ashmew2 says, the ext2/3/4fs family reserves 5% of its space for use by root. On a 9.85 GiB partition, this amounts to 0.4925 GB (470 MiB). This value is higher than one of the estimates of used space you got, but lower than another, so I suspect it's *part* of what you're seeing. You can adjust this value by using the tune2fs utility, as in "sudo tune2fs -m 0 /dev/sda2" to adjust the reserved space percentage to 0 on /dev/sda2. You should only do this when the filesystem is unmounted.
[*]Filesystems reserve a certain amount of space for their own necessary data structures. The single biggest eater of space on this score is the journal. I don't recall offhand precisely how large the journal is in an ext2/3/4 filesystem, so I'm not sure how much of what you're seeing can be attributed to this cause. Chances are it's at least part of the issue, though. You can find the journal size on any specific ext3/4fs volume by using dumpe2fs, as in 'sudo dumpe2fs /dev/sda2 | grep "Journal size"' to find the size of the journal on /dev/sda2.
[/LIST]


Of these three issues, only the 5% reserved space is something you can do anything about or should worry about, at least on most partitions. On very small partitions, such as a ~200 MiB /boot partition, the journal space can be enough of an issue that you might want to do without a journal entirely on such partitions. You'd do this by dropping back to ext2fs.

Also, keep in mind that different filesystems allocate space for files in different ways. Thus, if you go "shopping around" and test ext2fs, ext3fs, ext4fs, ReiserFS, JFS, XFS, and Btrfs (all the current Linux-native filesystems), you'll find that some give you more free space to start with than others; but because of allocation efficiency or inefficiency, the one with the most free space at the start might or might not enable you to store more files on it.

---

### Post by srs5694 on 2011-05-17
> **iconoclast hero said:**
> I am confused as to what you mean by my mixing IEEE and SI units.  I think that one utility reported the space one way and another utility reported it a different way...and to be perfectly honest, I didn't know that there was a distinction between IEEE and SI units.

I never used the word "mixing," or any synonym for it, that I can see. I did use the word "misused," which you might have misread as "mixed."

Different utilities can, as you say, use different units, and that can lead to confusion. Some utilities also use the *wrong* units (typically they use SI prefixes but report IEEE-1541 units), which is even worse. Some utilities offer an option of which type of unit to use. Such options are typically described in the documentation for the program.

---

### Post by iconoclast hero on 2011-05-17
> **srs5694 said:**
> I never used the word "mixing," or any synonym for it, that I can see. I did use the word "misused," which you might have misread as "mixed."

Different utilities can, as you say, use different units, and that can lead to confusion. Some utilities also use the *wrong* units (typically they use SI prefixes but report IEEE-1541 units), which is even worse. Some utilities offer an option of which type of unit to use. Such options are typically described in the documentation for the program.


I was referring to "I note also that you used the IEEE-1541 units in some places in your post, so you may already understand this." to make the point that I had no idea what the difference was.  My sincere apology.

---

