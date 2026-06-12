---
title: "RAID6 problems: 2 spares, 1 fail and array still active"
date: 2011-07-26
forum: General Help
---

### Post by roboa1983 on 2011-07-26
Hello,
I am currently having problems with my RAID6 partition. First two disks were having trouble (sde, sdf). Through smartctl I noticed there were some bad blocks, so first I set them to fail, and readded them so that the RAID array will overwrite these. 

Since that didn't work, I went ahead and replaced the disks. The recovery process was slow and I left things running overnight. This morning I find out that another disk (sdb) has failed, while the other two are deemed spares. Strangely enough the array has not become inactive:

md3 : active raid6 sdf1[15](S) sde1[16](S) sdak1[10] sdj1[8] sdk1[9] sdb1[17](F) sdan1[13] sdd1[2] sdc1[1] sdg1[5] sdi1[7] sdal1[11] sdam1[12] sdao1[14] sdh1[6]
25395655168 blocks level 6, 64k chunk, algorithm 2 [15/12] [_UU__UUUUUUUUUU]

I think this problem lies at the razor's edge since three disks are basically not working, and still, I don't know how the array can still be standing. I've been doing an extensive look up and have found that the --assume-clean command could help, but I'm still not sure since other references have shown that to be basically a coin toss.

Does anyone have any recommendations as the steps to take ahead with regards to recovery/fixing the problem? The disk is basically full so I haven't written anything to disk in the interim of this problem. 

Thanks!

---

