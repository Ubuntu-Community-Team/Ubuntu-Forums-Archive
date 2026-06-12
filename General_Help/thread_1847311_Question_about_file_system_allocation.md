---
title: "Question about file system allocation"
date: 2011-09-20
forum: General Help
---

### Post by gewone on 2011-09-20
**Hi!**

I'm running Ubuntu 10.10 (Maverick) on a machine. I have this mounted NTFS partition over there. The other night, I SFTP:ed to the Ubuntu box and pulled the whole /media/NTFSpartition/ over to a Windoze machine of mine.

When I was done, I decided to make a quick check for size match. This is where I go confuzed. I 'df -h' gives me 155 GB, whereas Windoze says the folder content is only 153,7 GB. I know that ext3 and NTFS use file allocation in different ways, but this shouldn't come to affect here, since both partitions are NTFS, right? Or am I missing out on something?

Oh, to make things even more complicated. I read about an alternative to the classic 'df', called 'di' (short for 'disk information'). I apt-get:ted this utility, and ran 'di -h'. The output looks just about the same as 'df -h', only that this one gives me 154,0 GB used, i.e. closer to what Windoze is reporting (153,7 GB), yet still not a perfect match.

So, guys. Am I missing out on something essential? Is it safe to assume that I have indeed managed to transfer all the files from my mounted NTFS partition on this 'Buntu box? I'd be much thankful for any sort of input on this.

***Cheers~***

---

### Post by dcstar on 2011-09-21
> **gewone said:**
> **Hi!**

I'm running Ubuntu 10.10 (Maverick) on a machine. I have this mounted NTFS partition over there. The other night, I SFTP:ed to the Ubuntu box and pulled the whole /media/NTFSpartition/ over to a Windoze machine of mine.

When I was done, I decided to make a quick check for size match. This is where I go confuzed. I 'df -h' gives me 155 GB, whereas Windoze says the folder content is only 153,7 GB. I know that ext3 and NTFS use file allocation in different ways, but this shouldn't come to affect here, since both partitions are NTFS, right? Or am I missing out on something?

Oh, to make things even more complicated. I read about an alternative to the classic 'df', called 'di' (short for 'disk information'). I apt-get:ted this utility, and ran 'di -h'. The output looks just about the same as 'df -h', only that this one gives me 154,0 GB used, i.e. closer to what Windoze is reporting (153,7 GB), yet still not a perfect match.
........

Find out exactly what block allocation sizes both NTFS partitions were formatted as and you may get an answer.

---

### Post by gewone on 2011-09-22
Much thanks for your reply dcstar!

How do I check block allocation size on NTFS volumes/partitions in the easiest way?

Regards~

---

### Post by gewone on 2011-09-25
Bump.

---

