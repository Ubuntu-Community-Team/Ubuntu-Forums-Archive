---
title: "mdadm and software raid5"
date: 2010-12-09
forum: General Help
---

### Post by unisubzero on 2010-12-09
[FONT=Calibri][SIZE=3]Hi guys,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT][SIZE=3][FONT=Calibri]I have a small question about mdadm and software raid5. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]For example if I have installed Ubuntu on a separate HDD (sda) with 4 x HDD (sd[bcde])configured as a raid5 members.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]If the first HDD with Ubuntu crash will I be able to restore my raid after replacing the failed HDD en installing Ubuntu again ?[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Or maybe I need to backup my mdadm.conf ?[/FONT][/SIZE]
 
Gr. Uni

---

### Post by unisubzero on 2010-12-14
[SIZE=3][FONT=Calibri]OK, I did test it in VMware environment by removing HDD with OS installed on it.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]During fresh install your array (mdx device) will be detected and all you need to do is to re-mount it like you normally do for your /home. [/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]So I hope this will be useful for someone and I guess it’s kind of solved.[/FONT][/SIZE]

---

### Post by amauk on 2010-12-14
Just to add
Yes, you can reassemble a linux software RAID drive on any other linux system

A backup of mdadm.conf is good (but not necessary, the UUID for the drive and it's layout can be determined by the mdadm control program)

---

