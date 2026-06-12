---
title: "gpart is telling me &quot;invalid arguement during seek for read on /dev/sda&quot;"
date: 2012-08-31
forum: General Help
---

### Post by Splodg3 on 2012-08-31
As the title says i am having problems with GParted it will not show me any partitions and shows the whole thing as "unallocated". When I look in the information section for the drive it displays the warning 
"invalid arguement during seek for read on /dev/sda"
i have 4 OS on my laptop Ubuntu, Windows XP, Lubuntu and Linux Mint, I can boot into all 4 of them.

Useful information:
blkid results show that the partitions are still there:
```
 haydn@haydn-Satellite-Pro-T130:~$ sudo blkid
/dev/sda2: LABEL="Windows XP" UUID="9CD8FCBED8FC982A" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu" UUID="38c289c7-c009-4c8b-8885-172f00c984c0" TYPE="ext4" 
/dev/sda6: LABEL="Lubuntu" UUID="ab244b09-997c-4627-9d9f-5f301e910672" TYPE="ext4" 
/dev/sda7: LABEL="Linux Mint" UUID="2eea42c8-a878-44fb-9fe6-dd2c349f6c10" TYPE="ext4" 
```Any help would be appreciated

Thanks 

Haydn

---

