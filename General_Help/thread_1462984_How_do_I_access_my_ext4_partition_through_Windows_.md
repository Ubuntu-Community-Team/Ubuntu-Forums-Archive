---
title: "How do I access my ext4 partition through Windows 7?"
date: 2010-04-26
forum: General Help
---

### Post by grf7291 on 2010-04-26
Hey guys I'm new to the forum and Ubuntu. Last night I installed Ubuntu 9.10 to its own partition and the partition was formatted as ext4. I was wondering how do I access data that's on my ext4 Ubuntu partition through my Win7 NTFS environment?

I'm on a HP HDX16 laptop with a single 500gb hard drive.

NTFS Win7 partition 431.48gb
ext4 Ubuntu partition 23.36gb
linux-swap partition 1.05gb
NTFS WinVista Recovery partition 9.85gb

---

### Post by dannyboy79 on 2010-04-26
have you looked into [http://www.fs-driver.org/](http://www.fs-driver.org/)
haven't tried to access ext4 partition in windows yet but I know that the fs-driver works with ext3 but haven't used in forever

---

### Post by viralmeme on 2010-04-26
I just Googled this ..

[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

[http://www.linuxjournal.com/article/9449](http://www.linuxjournal.com/article/9449)

---

### Post by oldfred on 2010-04-26
We usually recommend a separate /home so your data is not in the system partition. I have seen the same recommendation by windows users so when windows crashes your data is still in a good partition.

When I was dual booting I created a shared NTFS partition and put any data that I might share in that partition. I now use windows so little most of my data is in linux and I have no desire to use any of it from windows.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

