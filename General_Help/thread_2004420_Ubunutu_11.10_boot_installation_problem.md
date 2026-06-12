---
title: "Ubunutu 11.10 /boot installation problem"
date: 2012-06-15
forum: General Help
---

### Post by diiggidy on 2012-06-15
I recently installed Ubuntu 11.10 (which is now 12.04 after upgrading) onto my new SSD. I also have a different SSD for Windows 7, and a 500gb HDD for data. Since the first SSD is for Windows, I had no partitioning to do. For the new SSD, I created a GPT partition table with the following partitions:
/dev/sdb
2mb Bios_grub unformatted
40gb / (root) ext4
20gb / home ext4 

And then partitioned the HDD as such:
300gb ntfs Windows partition
90gb ext4 for /data
6gb swap

However, after installing everything I went back into Gparted to make sure everything was okay. I realized that when installing, somehow the partition I intended for /data was actually mounted as /boot and now has 1.37gb of data in it. I was told that I don't want a /boot partition for a SSD at all, but now have one. Also, the /boot is on my HDD, which I feel is defeating the purpose of having a SSD for fast boots. Anyways, I was wondering what I should do to solve this problem? I do not really want a separate partition for boot, and definitely not a 90gb for it. 

Also, I was wondering if I could combine the Windows 7 partition and the /data into one. What I mean by this, is would I be able to use one partition to store and use all my data from Windows AND ubuntu. So I could have all my music, videos, and documents in this partition to use in Windows and then link to from /home in Ubuntu? Is there somewhere I can read how to do this, or can somebody walk me through how to?

Thanks

---

