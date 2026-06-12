---
title: "How ot add a Ubuntu hard drive partition in Vista?"
date: 2009-12-11
forum: General Help
---

### Post by mharis on 2009-12-11
Hi, 

I installed ubuntu 8.04 in my pc and it was working fine, I had XP as the other OS and i was able to mount the FAT32 XP partitions into my Ubuntu.Then later on I got a windows Vista DVD so I removed XP and installed Vista over it, everything went fine but When Vista was installed, there was nowhere I could find my ubuntu. I installed Easy BCD to be able to get myself an OS choices menu at the startup, I was successul in that.

I hav 150 GB hard drive out of which I have made 3 partitions, C: is 40GB, D: is 50GB and E: is 60GB as in capacity. I can see only two of which in Vista (i-e C: and D: ), though all the partitions are visible and accesible in Ubuntu. 

I want to find a solution so that I can include that 60GB partition in Vista as well.

I am hopefull that I will be able to find some help here. :)

Thanks!

---

### Post by Bachstelze on 2009-12-11
Vista (or any version or Windows) canot access your Ubuntu partition. If it's ext2/3, there are drivers out there that are suppposed to do that, but they are quite unreliable, so I wouldn't recomment their use.

---

### Post by 73ckn797 on 2009-12-11
> **Bachstelze said:**
> Vista (or any version or Windows) canot access your Ubuntu partition. If it's ext2/3, there are drivers out there that are suppposed to do that, but they are quite unreliable, so I wouldn't recomment their use.


I have successfully used "Ext2IFS_1_11.exe" to read Linux files from Windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by mharis on 2009-12-11
> **73ckn797 said:**
> I have successfully used "Ext2IFS_1_11.exe" to read Linux files from Windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)


OmG that was so cool. I was able to have the partition in Vista using the driver you suggested without any difficulty!

Thanks so much guys for the help! :)

---

### Post by anaconda on 2009-12-11
> **Bachstelze said:**
> Vista (or any version or Windows) canot access your Ubuntu partition. If it's ext2/3, there are drivers out there that are suppposed to do that, but they are quite unreliable, so I wouldn't recomment their use.

actually the fs-driver is very reliable.

The only problem I ever had with it was (years ago, with an older version) when I copied files from XP to ubuntu, and the ubuntu disk got full.. Then some files corrupted, Everything was restored with fsck..

---

