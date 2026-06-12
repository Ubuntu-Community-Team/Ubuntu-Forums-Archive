---
title: "Lost and found folder on data partition"
date: 2012-09-14
forum: General Help
---

### Post by meanmrmustard on 2012-09-14
I remember reading somewhere that the lost and found folder on a non-bootable partition could be reduced in size.
I have a 3 TB disk used for backups and would like to reclaim all of the space I could from this folder.

Does anyone know where I can find out how this needs to be done?

Thanks

---

### Post by redmk2 on 2012-09-14
> **meanmrmustard said:**
> I remember reading somewhere that the lost and found folder on a non-bootable partition could be reduced in size.
I have a 3 TB disk used for backups and would like to reclaim all of the space I could from this folder.

Does anyone know where I can find out how this needs to be done?

Thanks

It's a tunable parameter of the utility **tune2fs** (-m).  I usually do this when formatting the partition.  Here is a [**_[COLOR="Blue"]google search[/COLOR]_**]("https://www.google.com/search?q=-m+reserved-blocks-percentage&btnG=Go!#hl=en&sugexp=les%3B&gs_nf=1&gs_mss=set%20reserved-blocks-percentage&tok=GezHKxhSZHMBuLdPADpmpg&pq=set%20reserved-blocks-percentage&cp=38&gs_id=411&xhr=t&q=set+reserved-blocks-percentage+tune2fs&pf=p&sclient=psy-ab&oq=set+reserved-blocks-percentage+tune2fs&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=540237b32d309954&biw=1208&bih=689") on the subject.  Here is [**_[COLOR="Blue"]another search[/COLOR]_**]("https://www.google.com/search?q=-m+reserved-blocks-percentage&btnG=Go!#hl=en&sclient=psy-ab&q=using++tune2fs&oq=using++tune2fs&gs_l=serp.3..0i30l2.199991.201197.3.202343.6.6.0.0.0.1.251.960.0j5j1.6.0.les%3B..0.0...1c.1.47Bl14E_25w&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=540237b32d309954&biw=1208&bih=689") on tune2fs.

---

### Post by meanmrmustard on 2012-09-14
Ah yes!
Thanks for jogging my memory.

---

