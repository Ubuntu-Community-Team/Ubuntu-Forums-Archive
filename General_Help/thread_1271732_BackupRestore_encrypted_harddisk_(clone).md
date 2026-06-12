---
title: "Backup/Restore encrypted harddisk (clone)"
date: 2009-09-21
forum: General Help
---

### Post by superubufan on 2009-09-21
Hello,  

I installed ubuntu with the alternate install cd and selected to **encrypt the root partition** (cryptsetup with lvm).  

Now I bought a new harddisk, because the old one was too small for me. I would like to clone (or b**ackup and restore**) my entire old disk so that I can just put it in the new disk.

I have some problems with that: 

[LIST]
[*] It's a laptops harddisk, so I need to move it to another external harddrive first and from there to the new one (since I don't have the right cables)
[*] I cannot just copy the partition information (so, clone the whole disk with dd) since the new one has a different layout
[*]  I cannot just make the partitions manually on the new harddisk, install cryptsetup on live system and put the data there because it's LVM and I fear that the system will not find the right logical volume after boot
[/LIST]
   
Can somebody help me and tell me the exact steps needed to do this all manually or even better name a tool that does all the work for me? I have looked at Partimage, Clonezilla etc. but they all don't support encrypted disks so far. 

Thanks,
superubufan

---

