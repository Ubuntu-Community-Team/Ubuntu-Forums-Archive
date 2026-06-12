---
title: "Disk partition"
date: 2010-05-29
forum: General Help
---

### Post by urndel on 2010-05-29
Hi everyone

I have currently used ubuntu for a few months now. I want to upgrade to 10.04 and want to improve my disk organisation. I have used linux on and of for about 3 years now and know a few things about computers. Partitioning itself is no prblem but i don't know what organisation would be good.
I already know that I will have a dedicated partition for /home
But I don't know about the rest. What things are good to give to a dedicated partition and what are the implication? And how does it need to be maintained?

Thanks in advance
Urndel

---

### Post by oldfred on 2010-05-29
It depends totally on you. I would expect if you get 4 responses you will get 8-10 recommendations on what is best.:)

Are you dual booting with windows. then a shared NTFS partition may be good to have. Separate /home makes it easier to to an upgrade to a new version as a clean install. I like having separate /data partition where most of my data is at. 

I originally just had root & swap with a small shared windows partition (then FAT now NTFS) for files that I wanted in both XP & Ubuntu. I also wanted to experiment with different installs and also use a new partition for each new update to Ubuntu. So I moved /home to a 100GB partition (I just bought a new drive, so I had lots of room) but then decided to move all the data folders to a /data partition. Now my /home is only 1GB (still in that 100GB as I have yet to clean that up). I have 20-25GB root partitions for last install, current install & beta of Ubuntu and space for several others that I hope to try.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

