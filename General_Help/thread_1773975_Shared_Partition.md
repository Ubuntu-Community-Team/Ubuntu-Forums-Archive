---
title: "Shared Partition?"
date: 2011-06-02
forum: General Help
---

### Post by [::AP::] on 2011-06-02
Hello - 

I am getting my Lenovo y470 tomorrow.
It comes with Windows 7 Home (64bit) preinstalled, on a 500 GB HDD. (~500GB, it's always a little less)

I know Ubuntu can mount the Windows partition, and with patching, vice-versa, but I have also read about using a  shared partition.

500 GB HDD
   * 130 GB - Windows 7
   * 70 GB - Ubuntu 
   * 300 GB - Shared

The shared partition will be where all documents, pictures, movies, music, etc. are stored. 

Question 1:
What file format? NTFS? With patching, Windows can read ext4, but not write? 

Question 2:
I have read conflicting opinions on the shared partition setup.
What are your opinions? What would you say is the most efficient setup?

Thank you,

[::AP::]

---

### Post by oldfred on 2011-06-02
I am a fan of smaller system partitions and larger data partitions. I would make the shared NTFS. Do not write into your Windows install from Ubuntu unless you have to for repairs. Windows just does not like too much writing and the NTFS driver in Ubuntu does not hide any system files or folders and makes it too easy to accidentally modify windows. If you want to read from your Win7 partition set it read only to avoid issues.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

These will provide the additional detailed steps:
HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu
[http://ubuntu.swerdna.org/ubuntfs.html](http://ubuntu.swerdna.org/ubuntfs.html)
Auto mount NTFS Partition
[http://ubuntuforums.org/showpost.php?p=7342606&postcount=10](http://ubuntuforums.org/showpost.php?p=7342606&postcount=10)

this is now older but reviews some of the issues:
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by [::AP::] on 2011-06-02
Thanks for the response. 

I probably won't share apps, like the LifeHacker article stated, but I appreciate the links. 

I am just hoping that the Ideapad y470 doesn't insist on having recovery partitions, etc. I can burn that to a disk.

Thanks again, 

[::AP::]

---

